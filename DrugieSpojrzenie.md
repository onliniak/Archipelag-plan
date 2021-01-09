Zapamiętać: trzymać ludzi chaotycznych z dala od szeroko-rozumianej architektury.

## Edytor

Najważniejszą częścią wersji podglądowej będzie edytor low-code. 
Ekran podzielony na 3 części: 1:2.6:1. Trzecia część z przyciskami, które odkrywają ukryte panele. 
Powyżej wyszukiwarka. Użytkownik wpisuje w niej słowa kluczowe, przeglądarka próbuje pobrać plik json schema z 
example.com/schemas/editor/{keyword}.json 

Plik json schema wygląda mniej więcej tak: 
```
title: nazwa sekcji,
properties:
  textarea: [
    type: boolean,
    regex: regex (opcjonalnie)
  ],
  input1: [
    type: number,
    minlength: 2,
    maxlength: 10
  ], 
  send: [
    type: string
  ]
```
Na jego podstawie przeglądarka tworzy odpowiednie przyciski. 
Gdzie title to nazwa widocznego przycisku, a properties to przyciski ukryte, które pokażą się po kliknięciu.
https://onliniak.github.io/Archipelag-dev/

Po wypełnieniu formularza, jest on przesyłany do serwera, który sprawdza jego zgodność z kolejnymi plikami json schema. 
Na przykład formularz może tworzyć plik monster123.json, który musi być zgodny z example.com/schemas/monster.json. 
Następnie plik jest zapisywany na serwerze lub osobnym serwerze statystycznym (w tym wypadku GitHub).

## Podgląd

I w drugą stronę, po przejściu na stronę example.com/test, przeglądarka wysyła żądanie GET do example.com/schemas/test.json. 
Jeśli plik istnieje, przetworzy go na kod html. Cała strona składa się z znanych komponentów jak zdjęcie, tabela, czy tekst. 
Plik json zawiera listę komponentów do wykorzystania, w określonej kolejności. I tu pojawia się problem, 
komponenty mają pełne zaufanie do plików konfiguracyjnych. Na chwilę obecną rozwiązuję to używając 
TextNode kiedy to tylko możliwe. 
