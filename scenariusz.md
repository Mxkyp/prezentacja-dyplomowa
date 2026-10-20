---
id: scenariusz
aliases: []
tags: []
---
Zreferowanie osiągnięć z projektu dyplomowego - 7,8 minut

1. Umotywować wybór tematu, odwołując się do istniejących rozwiązań lub osobistych problemów, które inne rozwiazania nie rozwiązują
Trzeba założyć że komisja nic o pracy nie wie, żeby

2. Referujemy projekt inżynierski

3. Strategia rozwiązania, jak do tego się przyłożyliśmy

4. Rezultat, jaki jest outcome, implementacja ogólnie

5. Wnioski i spostrzeżenia (istotny element prezentacji) – czy cel się udało osiągnąć, jakie były trudności i jak się z nimi udało poradzić

Sama prezentacja też 7,8 minut więc 7,8 slajdów
Warto zadbać o estetykę prezentacji. I sprawdzić czy nie ma błędów na prezentacji (ortograficznych, literówek itp.)

# Wstęp
Szanowno komisja, tematem mojej pracy inżynierskiej jest interaktywna platfroma do nauki algorytmów bioinformatyki której nadałem imię Algobio.

Interaktywna platfroma tzn. umożliwiająca użytkownikom naukę bezpośrednio w przeglądarce.
## Motywacja wyboru i luka rynkowa


## Uwagi gemini
To jest zdecydowanie najlepsza zmiana, jaką można zrobić w sekcji Rezultat implementacji. Na obronie inżynierskiej komisja chce zobaczyć, że system naprawdę powstał i działa –
  zrzuty ekranu robią 10x lepsze wrażenie niż lista punktowana opisująca interfejs słowami, a jednocześnie działają jak bezpieczne mini-demo (bez ryzyka problemów z siecią na
  sali).
  ──────
  ### Jak to najlepiej ułożyć w prezentacji?

  #### 1. Technika: Karuzela na jednym slajdzie (\only<1>, \only<2>, \only<3>...) vs osobne slajdy

  Polecam jeden slajd z krokami \only<1-N>:

  • W motywie Warsaw na górnym pasku nawigacyjnym nie namnożą się dodatkowe kropki,
  • Klikasz strzałkę w prawo i płynnie przełączasz kolejne ekrany aplikacji,
  • Każdy ekran ma swój wyraźny pasek tytułowy (np. 1/4: Katalog problemów bioinformatycznych) + duży, wycentrowany zrzut .png w estetycznej ramce.

    +-----------------------------------------------------------------------------------+
    | Rezultat pracy inżynierskiej -- zrealizowana platforma AlgoBio			|
    +-----------------------------------------------------------------------------------+
    |  +-----------------------------------------------------------------------------+  |
    |  |  [ 2/3 ]  Interaktywne środowisko pracy (CodeMirror 6 + wyniki testów)      |  |
    |  +-----------------------------------------------------------------------------+  |
    |  |                                                                             |  |
    |  |                                                                             |  |
    |  |			[ ZRZUT EKRANU: ide_view.png ]                       |  |
    |  |                   (dopasowany automatycznie do wysokości)                   |  |
    |  |                                                                             |  |
    |  |                                                                             |  |
    |  +-----------------------------------------------------------------------------+  |
    +-----------------------------------------------------------------------------------+

  #### 2. Proponowana sekwencja ekranów (naturalna ścieżka użytkownika – ok. 60–90 sekund opowiadania):

  1. Widok 1: Katalog problemów bioinformatycznych – pokazujesz listę zadań, filtrowanie, poziomy trudności.
  2. Widok 2: Interaktywne IDE (opis + edytor CodeMirror 6 + panel testów Run/Submit) – serce platformy, nawiązujące bezpośrednio do naszego schematu ze Slajdu 2.
  3. Widok 3: Grywalizacja i profil użytkownika – dzienna seria (streak), roczna mapa aktywności (heatmap) oraz statystyki.
  4. (Opcjonalnie) Widok 4: Panel administratora – globalne statystyki platformy i zarządzanie zadaniami.
  ──────
  ### Jak działamy?

  1. Ile zrzutów ekranu chcesz pokazać i jakie mają (lub będą miały) nazwy plików .png (np. w podkatalogu img/ lub bezpośrednio w katalogu projektu)?
  2. Czy robimy to jako kroki \only<1-N> w obrębie jednego slajdu, czy wolisz osobne slajdy?
