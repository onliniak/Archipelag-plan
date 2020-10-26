# Archipelag-plan
Podsumowanie wszystkich informacji zebranych do tej pory.

Dopiski:
  - Ideologia
    - Jeśli projekt jest płatny to szybkość wykonania zawsze jest ważniejsza od jakości, powiem nawet że im gorsza jakość tym lepiej (patrz: płatne wtyczki do WordPressa). Ale jeśli projekt jest darmowy to należy się nim zająć tylko i wyłącznie wtedy, kiedy ma się pewność że posiadane umiejętności są wystarczające do napisania średnio-dobrej jakości kodu który będzie wydajny i łatwy w przyszłym zarządzaniu. Jeśli w trakcie projektowania lub pisania pojawią się trudności, projekt należy wstrzymać na miesiąc.

## Wprowadzenie 

Archipelag to planowany od roku (→ Ideologia) Eksperymentalny Elastyczny Silnik Gier Tekstowych. Zaczynał jako próba przepisania Vallheru Engine na PHP7, a stał się odpowiedzią na [Twine](https://twinery.org/). 

Pierwotnym celem projektu było stworzenie alternatywy dla Amorionu. Po pierwszych nieudanych próbach pojawił się pomysł napisania całego silnika od zera.
Była szansa na rozwiązanie sprawy jak trzeba (silnik powstaje osobno i gra osobno) ale stanęło na tworzeniu całości krok po kroku. Czyli najpierw silnik, potem udostępnienie go wszystkim chętnym, przełączenie się na tworzenie tej konkretnej gry i prowadzenie jej do końca. 

Podstawowym zarzutem dla Vallheru jest brak nowych graczy. Potem mamy wolno wczytujące się strony i wreszcie długie oczekiwanie na administratorów by cokolwiek zmienić. 
Celem Archipelagu jest stworzenie prototypu nowej gry, która z jednej strony będzie mniej nudzić, a z drugiej nie zniechęci starych graczy. 

Plan jest taki: 

Zamiast obciążać serwer, wszystkie teksty i inne "nieruchome" części gry będą leżeć na statycznym hostingu jak GitHub Pages. Serwer przechowuje tylko i wyłącznie stan, czyli: logowanie, rejestracja, zmiana ekwipunku, zmiana statystyk, zmiana pieniędzy, walka. Powinno to z miejsca przyśpieszyć działanie aplikacji i ograniczyć zużycie zasobów serwera.

Co do nowych graczy proponuję włączenie elementów strategicznych jak: zmniejszenie ilości pieniędzy przy sobie do UInt8 (255) i pieniędzy w banku do UInt16 (65535); zlikwidowanie magicznego klonowania rynku → przedmiot wystawiony na sprzedaż w mieście A zostaje w mieście A; wprowadzenie ograniczonych zasobów jedzenia i wody, po których wyczerpaniu gracze będą zmuszeni do szukania nowego domu; ataki graczy-bandytów; ktoś tam zaproponował faktorie czyli w określonych miejscach mamy określone zasoby, po których zdobyciu dostajemy premię do energii dla wszystkich członków klanu; bitwy o faktorie w stylu taktycznym (Forge of Empires); śmierć → zamiast magicznego uzdrowienia w szpitalu tracisz swoją postać i albo zaczynasz od nowa z 50% punktów postaci do rozdania albo jeśli masz rodzinę i dzieci przełączasz się na syna/córkę (którzy dziedziczą 75% statystyk z ojca i matki); osiągnięcia.

Pierwsze reakcje to zmiany może i są dobre ale wprowadzą za duże zamieszanie … więc trzeba będzie albo jeszcze nad tym pomyśleć albo wprowadzić osobny łagodny świat bez przemocy i nagłych śmierci. Oczywiście wybór mechaniki nie może stać się przeszkodą w komunikacji więc powinna być możliwość wysyłania wiadomości i udziału w forach między światami.

### Cele

Framework:
  - Modyfikacja gry nie może wymagać posiadania umiejętności 'technicznych'
  - Szybki czas wczytywania strony
  - Minimalna ilość konfiguracji
  - Całą stroną techniczną (hosting itp) zajmujemy się my (czyli mamy Oprogramowanie jako Usługę).
    - Dotyczy tylko większości. Mniejsza część musi mieć możliwość zainstalowania tego na własnym serwerze.
  - Przeznaczenie: 
    - Czytanie tekstu
    - Czytanie tekstu + dokonywanie wyboru
    - Dodawanie zdjęć i filmów
    - Dodawanie własnych zmiennych i dostęp do bazy danych
   
Opowieść:
  - Dobrze nakreślone miejsce i czas akcji
  - Krótka historia
  - Oparcie na miastach
  - Zdobywanie kolejnych poziomów
    
## Wstępny podział

```
Użytkownik → tworzy → plik tekstowy #Opowieść
                            ↓
                 który przekazywany jest
                            ↓
                       Kompilatorowi ↔ przekazywany jest do ↔ parser YAML 
                            ↓
           w pamięci RAM powstaje gigantyczna tablica 
                            ↓
                która implementowana jest przez
                            ↓
             funkcja1    funkcja2    funkcja 3    …
                            ↓
                    pobiera instrukcje ← z pliku definicji
                            ↓
                         zamienia
                            ↓
                       na kod źródłowy
                            ↓
                         zapisuje → wysyła
                                      ↓
               lub inne pliki ↔ na hosting ↔ jako plik functions.ext
                                      ↓
                                 gdzie czeka
                                      ↓ 
                                 web framework → uruchamiający → serwer #Fundament
                                                                    ↓
                                                                wyświetla
                                                                    ↓
                                                                  stronę
```

Widzę to jako trzy osobne części:
  1. Tryb Opowieści
  2. Kompilator
  3. Fundament
  
### Tryb Opowieści 

Tryb Opowieści pozwala na odzwierciedlenie dowolnej strony w formie łatwego do odczytania pliku YAML (lub podobnego). Gdzie za pomocą ograniczonej liczby poleceń (coś w stylu Python Kivy KV) można zapełnić go treścią. 

Czyli powiedzmy że piszę 

```
#Hello.yaml

image:
  photo.png
 
text:
  Hello World!
```

Wrzucam do kompilatora, uruchamiam serwer i widzę napis Hello World i zdjęcie pod adresem moja.strona/hello.

Jeśli chodzi o porządek to wszystkie zdjęcia i teksty będą leżeć w określonych katalogach. Polecenia będą przekazywane w oddzielnych plikach zwanych definicjami. Definicja dotyczy określonego języka programowania i jest napisana w tym języku, czyli na przykład piszę w Ruby i chcę żeby definicja img zwracała kod HTML:

```
def image(filename) do
  filepath = File.expand_path('/images', filename)
  img = '<img src"#{filepath}" loading="lazy">'
  return img
end
```

Na razie wygląda to tak, jak wyjdzie już beta to pomyślę nad jakimś edytorem wizualnym. Chyba że wcześniej ktoś już taki stworzy.

### Kompilator

Kompilator bierze pliki tekstowe i na ich podstawie tworzy pliki źródłowe. Będzie wykonywany na maszynach wirtualnych, więc nie musi być super wydajny (przynajmniej na początku). Widziałem wiele usług CI/CD, które udostępnią bezpłatnie maszynę wirtualną z 4-8 GiB RAMu i procesorem dwu/cztero -rdzeniowym.

Kompilator korzysta z interfejsów. Wczytuje zawartość pliku do pamięci, a następnie na podstawie odpowiedniego polecenia zamienia go w inny rodzaj plików. Początkowo będzie obsługiwać zamianę na zapytania SQL, generowanie statycznego kodu HTML/CSS/JS + router oraz generowanie funkcji w jeszcze nieokreślonym języku programowania.

### Fundament

Kompilator wyrzuci funkcje ale potrzebny jest jeszcze web framework. I tu pojawia się fundament, czyli przygotowany wcześniej kod uruchamiający silnik w danym środowisku np. w przeglądarce internetowej. 

Oczywiście nic nie stoi na przeszkodzie, by w przyszłości stworzyć wersje desktopowe, czy mobilne. Wystarczy przygotować nowy fundament i gotowe. 

