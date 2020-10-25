# Archipelag-plan
Podsumowanie wszystkich informacji zebranych do tej pory.

Dopiski:
  - Ideologia
    - Jeśli projekt jest płatny to szybkość wykonania zawsze jest ważniejsza od jakości, powiem nawet że im gorsza jakość tym lepiej (patrz: płatne wtyczki do WordPressa). Ale jeśli projekt jest darmowy to należy się nim zająć tylko i wyłącznie wtedy, kiedy ma się pewność że posiadane umiejętności są wystarczające do napisania średnio-dobrej jakości kodu który będzie wydajny i łatwy w przyszłym zarządzaniu. Jeśli w trakcie projektowania lub pisania pojawią się trudności, projekt należy wstrzymać na miesiąc.

## Wprowadzenie 

Archipelag to planowany od roku (→ Ideologia) Eksperymentalny Elastyczny Silnik gier tekstowych. Zaczynał jako próba przepisania Vallheru Engine na PHP7, a stał się odpowiedzią na [Twine](https://twinery.org/). 

Naszym zadaniem jest napisanie czegoś na kształt Amorionu. Mamy wolną rękę jeśli chodzi o wprowadzane zmiany ale nie możemy nikogo do nich zmuszać. Dla zleceniodawcy liczy się demo/opowieść, a nie sam framework. Ma być możliwość ewentualnego dostosowania do nowych warunków i oczekiwań.

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

Widzę to jako trzy osobne części:
  1. Tryb Opowieści
  2. Kompilator
  3. Fundament
    - Serwer
    - Klient
  
### Tryb Opowieści 

Tryb Opowieści to nakładka wizualna, która na podstawie łatwych do odczytania plików YAMLa (lub podobnych) stworzy kod aplikacji. 

### Kompilator

Kompilator bierze pliki tekstowe i na ich podstawie tworzy pliki źródłowe. Będzie wykonywany na maszynach wirtualnych, więc nie musi być super wydajny (przynajmniej na początku). Zakładamy, że będzie miał do dyspozycji Quad-Core CPU i 8 GiB RAMu. 

Kompilator korzysta z wzorca Strategii. Wczytuje zawartość pliku do pamięci, a następnie na podstawie odpowiedniego polecenia zamieni je w inny rodzaj plików. Początkowo będzie obsługiwać zamianę na zapytania SQL i tworzenie funkcji w jednym języku programowania. Potem pomyśli się nad resztą. 

### Fundament

Kompilator wyrzuci funkcje ale potrzebny jest jeszcze web framework. I tu pojawia się fundament, czyli przygotowany wcześniej kod uruchamiający silnik w danym środowisku np. w przeglądarce internetowej. 
