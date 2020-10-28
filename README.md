# Archipelag-plan
Podsumowanie wszystkich informacji zebranych do tej pory.

Dopiski:
  - Ideologia
    - Jeśli projekt jest płatny to szybkość wykonania zawsze jest ważniejsza od jakości, powiem nawet że im gorsza jakość tym lepiej (patrz: płatne wtyczki do WordPressa). Ale jeśli projekt jest darmowy to należy się nim zająć tylko i wyłącznie wtedy, kiedy ma się pewność że posiadane umiejętności są wystarczające do napisania średnio-dobrej jakości kodu który będzie wydajny i łatwy w przyszłym zarządzaniu. Jeśli w trakcie projektowania lub pisania pojawią się trudności, projekt należy wstrzymać na miesiąc.

## Wprowadzenie 

Archipelag to planowany od roku (→ Ideologia) Eksperymentalny Elastyczny Silnik Gier Tekstowych. Zaczynał jako próba przepisania Vallheru Engine na PHP7, a stał się odpowiedzią na [Twine](https://twinery.org/). 

Pierwotnym celem projektu było stworzenie alternatywy dla Amorionu. Po pierwszych nieudanych próbach pojawił się pomysł napisania całego silnika od zera.
Była szansa na rozwiązanie sprawy jak trzeba (silnik powstaje osobno i gra osobno) ale stanęło na tworzeniu całości krok po kroku. 

Podstawowym zarzutem dla Vallheru jest brak nowych graczy. Potem mamy wolno wczytujące się strony i wreszcie długie oczekiwanie na administratorów by cokolwiek zmienić. 
Celem Archipelagu jest stworzenie prototypu nowej gry, która z jednej strony będzie mniej nudzić, a z drugiej nie zniechęci starych graczy. 

Plan jest taki: 

Zamiast obciążać serwer, wszystkie teksty i inne "nieruchome" części gry będą leżeć na statycznym hostingu jak GitHub Pages. Serwer przechowuje tylko i wyłącznie stan, czyli: logowanie, rejestracja, zmiana ekwipunku, zmiana statystyk, zmiana pieniędzy, walka. Powinno to z miejsca przyśpieszyć działanie aplikacji i ograniczyć zużycie zasobów serwera.

Co do nowych graczy widzę szansę w ciągłym napięciu i ekonomii jak na rzemieślnika przystało.

Oczywiście nie wszystkim podobają się zmiany, uważając że nawet jeśli część z nich jest dobra to zmienianie przyzwyczajeń jest najgorszym co można zrobić. Więc najprawdopodobniej powstaną dwa światy. Jeden nastawiony na elementy survivalu i jeden łagodny. 

- Śmierć
  - Można ją pokonać na 3 sposoby:
    - Jeśli w mieście jest działający szpital to można zapłacić za wskrzeszenie (jeśli władca włączy taką opcję)
    - Jeśli poległy zostanie odnaleziony przez innych i sprowadzony do placówki medycznej, istnieje pewna szansa że wyjdzie z tego cało
    - Jeśli ma rodzinę, to może przełączyć się na swojego syna/córkę
      - Dziecko otrzymuje po połowie punktów postaci od matki i ojca.
    - Jeśli wszystko inne zawiodło, powraca z 75% punktów postaci
- Inflacja
  - Maksymalna ilość pieniędzy w sakiewce to UInt8 (255)
  - Maksymalna ilość pieniedzy w banku to UInt16 (65535)
- Transport
  - Koniec z automagicznym pojawianiem się przedmiotów na wszystkich rynkach świata
  - Od teraz jeśli chcesz sprzedać przedmiot w mieście X to musisz go tam zanieść
  - Albo zamówić transport
    - Publiczne karawany (sponsorowane przez króla) wyruszają raz na 24 godziny
    - Prywatni gracze mogą zbudować swoje mini przedsiębiorstwo transportowe
      - W takim przypadku mogą też przewozić innych graczy
- Inn
  - W tej wersji znane z Amorionu Karczmy, Noclegownie i Fontanny trafiają do jednego budynku
  - Inn pozwala na jedzenie (raz na 8 godzin, mało energii) i spanie (raz na dzień gry, dużo energii)
  - Oraz zakładanie pokoi na czacie
  - Może być prowadzony przez graczy
  - Publiczne zajazdy są dostępne w każdym większym mieście ale niekoniecznie oferują aż takie wygody jak prywatne
  - W zamyśle będą przejmowane przez graczy fabularnych, którzy będą prowadzić tu swoje opowieści
- Zbójcy
  - Od teraz gracze mogą prowadzić romantyczny żywot rozbójnika
  - Karawany krążą zawsze po tej samej trasie
  - Ich ruchy są śledzone przez odpowiednie placówki pocztowe
  - Podobnie z patrolami strażników ale oni podlegają pod wojsko
  - Niewielka grupa może zaczaić się, zaatakować i uciec z łupem
  - Im więcej ludzi, tym łatwiej ich wykryć
  - Im więcej strażników tym większa szansa na wykrycie
  - Nie chcę budzić złudnych nadziei że w pierwszej wersji będziemy mieć super AI
  - Najprawdopodobniej liczba strażników i złodziei zostanie ograniczona
- Skarbiec
  - Wykorzystywany do:
    - Utrzymania sklepów i dróg
    - Zapewniania czasowych lub stałych premii na terenie określonego miasta
    - Podwyższania/obniżania opłat targowych i podatków od sprzedaży w sklepach
    - Handlu z innymi królestwami
    - Fundowania loterii i konkursów
    - Utrzymania urzędników państwowych
    - Kupna NPCów dających stały przyrost surowców w magazynach.
- Królestwo
  - Istnieje kilka królestw
  - W ciągu gry można założyć własne
    - Pamiętając, że wszystkie budynki należy założyć od zera
    - Co wymaga posiadania pieniędzy i transportu niezb≥ędnych surowców
    - W domyśle na taki luksus pozwolą sobie jedynie klany
  - Maksymalna liczba państw ograniczona
- Faktoria handlowa
  - To akurat nie mój pomysł
  - Na mapie mamy kilka miejsc z surowcami specjalnymi
  - Po zbudowaniu niezbędnej infrastruktury można czerpać z nich korzyść
  - Wtedy cały klan otrzymuje premię do energii.
- Wojna
  - Miasta i Faktorie mogą zostać zaatakowane
  - Przypomina to nieco bitwę o forty w The West
  - Gracze mają 24 godziny na przybycie do określonej lokacji
  - Przed bitwą można atakować innych graczy
    - Ale istnieje ryzyko że zwróci się uwagę całej drużyny
    - Złodziej ma pewną premię do uniknięcia wykrycia
    - Drużyna atakującego nie pomaga w ataku
    - Ale drużyna obrońcy już tak
  - Po upływie czasu przenosimy się na mapę taktyczną
  - Bitwę rozpoczynają łucznicy
  - Następnie magowie
  - Wojownicy przystępują do ataku
  - Chodzicie po kwadracikach, atakujecie się i tak dalej
  - Po 15 minutach jest 5 minutowa przerwa (chyba że większość się zgodzi by kontynuować)
  - Bitwa się kończy gdy wszyscy padną.
  - Żeby wyrównać szansę: 
    - Jeśli atakujący mają mocniejsze postacie, to obrońcy dostają premię do obrony
    - Jeśli mają liczniejszą armię to otrzymują premię do ataku
    - Jeśli silniejszy wygra to przegrani dostają premię do doświadczenia
    - A jeśli mają wyrównane szanse to wygrani dostają premię do doświadczenia
  - Limitów ataków nie ma
- Osiągnięcia

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

```ruby
def image(filename) do
  filepath = File.expand_path('/images', filename)
  img = '<img src"#{filepath}" loading="lazy">'
  return img
end
```

Na razie wygląda to tak, jak wyjdzie już beta to pomyślę nad jakimś edytorem wizualnym. Chyba że wcześniej ktoś już taki stworzy.

### Kompilator

Kompilator bierze pliki tekstowe i na ich podstawie tworzy pliki źródłowe. Będzie wykonywany na maszynach wirtualnych, więc nie musi być super wydajny (przynajmniej na początku). Widziałem wiele usług CI/CD, które udostępnią bezpłatnie maszynę wirtualną z 4-8 GiB RAMu i procesorem dwu/cztero -rdzeniowym.

Kompilator korzysta z interfejsów. Wczytuje zawartość pliku do pamięci, a następnie na podstawie odpowiedniego polecenia zamienia go w inny rodzaj plików. Początkowo będzie obsługiwać zamianę na zapytania SQL, generowanie kodu statycznego Jekyll (GitHub Pages) oraz generowanie funkcji w jeszcze nieokreślonym języku programowania.

### Fundament

Kompilator wyrzuci funkcje ale potrzebny jest jeszcze web framework. I tu pojawia się fundament, czyli przygotowany wcześniej kod uruchamiający silnik w danym środowisku np. w przeglądarce internetowej.

Oczywiście nic nie stoi na przeszkodzie, by w przyszłości stworzyć wersje desktopowe, czy mobilne. Wystarczy przygotować nowy fundament i gotowe. 

## Pozostałe

### Poszukiwania

Wymyśliłem sobie, że zdejmę potrzebę szukania hostingu. Przez jakiś czas rozglądałem się po hostingach w chmurze; Heroku może być dobrym wyjściem ale nie można go używać przez całą dobę i nie ma opcji zapisu do plików; Azure byłoby w sam raz ale wymaga karty kredytowej; IBM Cloud wydaje się dobrym wyjściem; Gigalixir to Heroku które nigdy nie zasypia ale dają jedynie 1GB przepustowości. W końcu znalazłem opcję zostania resellerem resellera i otrzymania bieda hostingu za $0.00. Jedyną wadą jest ograniczenie wyświetleń do 50k, potem trzeba płacić jakieś drobne co miesiąc. Myślę że na początek to odpowiedni wybór.

Kompilator będzie w Krysztale → jest językiem kompilowanym, szybki, mało zasobożerny i ma natywne wsparcie dla YAMLa. Przynajmniej na początku.

Część kliencka wymaga szybkiego i lekkiego frameworka SPA z wbudowanym routerem. Reacty, Angulare i cała reszta odpada. Myślałem nad Aurelia Framework lub DataFormsJS + WebComponents. Najprawdopodobniej szybciej będzie skorzystać z generatora stron statycznych. 

Część serwerowa może się składać dosłownie z czegokolwiek. Baza danych będzie w SQLite3 WAL, a serwer musi mieć możliwość wyświetlania JSON.
Jeszcze wymaga to kilku testów ale na chwilę obecną najbardziej obiecująca jest Symfonia5 (PHP). 

Jeśli chodzi o koszty to tak długo jak nie muszę wydawać ani grosza, wszystko jest bezpłatne. Chyba że ktoś ma wyrzuty sumienia to potem pomyśli się nad opcją włączenia reklam.

### Logowanie

Mamy rok 2020, a hasła miały zniknąć z 5 lat temu. Dziś, mamy już standard WebAuthn umożliwiający logowanie się za pomocą odcisków palców i kluczy cyfrowych FIDO U2F. Archipelag jako jeden z pierwszych zamierza uczynić go głównym sposobem uwierzytelniania. Oczywiście dla biedniejszych (koszt takiego urządzenia to 100-300zł) nadal będzie możliwość logowania się hasłami.

## Archipelag Gra

### Miejsce akcji

Akcja rozgrywa się na tytułowym archipelagu, na który składają się dwie główne wyspy i kilka mniejszych.

Najdalej na wschód położona wyspa jest górzysta, pochodzenia wulkanicznego. Po dziś dzień można podziwiać krater z lawą. Znajdziemy na niej mnóstwo surowców mineralnych, metali szlachetnych, wieczny lodowiec w wysokich partiach masywu górskiego i rozległą pustynię w centralnej części terenu. 

Na zachód od niej znajdziemy płaską, piaszczystą wyspę koralową oddaloną od sąsiadów wąskim pasem wody o szerokości 10km. Zalesiona, patrząc z lotu ptaka ma kształt końskiej głowy. Znajdziemy tu sztuczny, miedziano-kamienny okrągły "basen" o średnicy 1km i głębokości 20m, wypełniony słodką wodą z roztopionego lodu. Czyli ma z 30 000 litrów. Teren nad tym "jeziorem" zajmuje osada, od której rozchodzą się promieniście pola uprawne wypełnione ziemią wulkaniczną.

Dalej na zachód znajdziemy kilka mniejszych wysepek o średnicy 300-500m. 

Od południa mamy ciepłe prądy morskie podwyższające temperaturę wybrzeża do nawet 30°C, od północy temperatura na plaży zbliża się do 20°C. Temperatura w górach zbliża się do zera.

Parę wieków wcześniej pewna sekta została zmuszona do opuszczenia swoich ziem, w obawie przed prześladowaniami. Byli inżynierami i medykami, oskarżanymi o czary. Zrobili zrzutkę, wynajęli statek i odpłynęli na drugą stronę planety. Tutaj dzięki całkowitej niezależności od średniowiecznej kultury i sporej ilości wszelkich metali/minerałów udało im się dojść do Newtona i de Vaucansona (XVII/XVIII). Obecnie zamieszkują wyspę koralową.

Tymczasem na świecie nastał wiek XVI, pewien król znudzony podbiciem wszystkich ziem znanego mu świata (coś jak Alexander Macedoński), wysyła okręty wojenne w celu zajęcia nowych ziem. Niestety burza pokrzyżowała im plany i wylądowali bezradni na naszym archipelagu. Jako jeden z rozbitków musisz walczyć o przetrwanie albo znaleźć sposób na powrót do domu.

#### Rzemiosło

Rzemiosło korzysta z tzw. wzoru magicznego, czyli takiego który napisałem i zapomniałem co właściwie znaczył. 

- Skill = Siła, Zręczność … 
- Trait = Kowalstwo, Stolarstwo …
- Ilość wykonanych przedmiotów zależy od poziomu, a umiejętności liczą się tyle co nic

```ruby
class Player
  def artisan(itemlvl, profession, attribute)
    user = request.POST['user']
    playerlvl = DB[:Players][email: user][lvl]
    trait = DB[:Players][email: user][attribute]
    skill = DB[:Players][email: user][profession]
    score = Math.hypot(trait, skill)
    power = Math.log(energy, score)*playerlvl/10*energy
    difficulty = power/itemlvl
    puts difficulty.to_i
  end
end


# Wraz z zwiększającym się lvlem, maleje ilość wymaganej energii.
# Jednocześnie wymuszam szybkie podniesienie lvla powyżej 10.

====== Demo w javascripcie ======
https://jsitor.com/-rcZEAJzx
```
##### Kowalstwo i walka bronią białą
Podstawą kowalstwa jest pozbycie się znanego od Final Fantasy podziału na 100 000 mieczy różniących się tylko nazwą. 

Od teraz mamy aż 3 rodzaje broni:
- Krótką (noże)
- Długą (miecze, szable)
- Drzewcową (włócznie, oszczepy)

Każda z nich ma odpowiednie atrybuty:
- Waga - Czyli ile siły musi mieć postać, by jej użyć
- Skrytość - Czy może być wykorzystana w atakach skrytobójczych ?
- Długość - Ile zręcznosci wymagane jest by móc się nią posługiwać
- Zakrzywienie - Zmniejsza zręczność i siłę wymaganą do posługiwania się bronią
- Wyważenie - Zmniejsza zręczność i siłę, zależy od umiejętności kowala
- Cięcie - Czy można nią normalnie walczyć ? (Patrz niżej)

Mamy 3 rodzaje ataku: 
- Pchnięcie - Odpowiednik silnego ataku
- Cięcie - odpowiednik normalnego ataku
- Rzut - jeśli trafisz dobrze to masz krytyka, a jeśli źle to tracisz broń
