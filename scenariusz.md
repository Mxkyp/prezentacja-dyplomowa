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

Aby nie odwracać się do ekranu, zapamiętaj prezentację jako **4 logiczne bloki połączone łańcuchem przyczynowo-skutkowym**:
**PROBLEM RYNKOWY (2 slajdy) -> PRODUKT (1 slajd, 5 kliknięć) -> ARCHITEKTURA (2 slajdy) -> GŁÓWNY PROBLEM INŻYNIERSKI (3 slajdy)**.

```text
[1. Tytuł]
   │
   ▼
=== BLOK I: DLACZEGO TO ZROBIŁEM? (Motywacja) ===
[2. Paradygmat LeetCode (3 kliknięcia: Szablon -> Run -> Submit)]
   │  Kotwica: "Jak dziś uczy się algorytmów? Przeglądarka, czysty kod w klasie, Run i Submit."
   ▼
[3. Siatka 8 branż (Quant, ML, DevOps... -> Bioinformatyka ???)]
   │  Kotwica: "Każda branża ma swojego LeetCode'a, a bioinformatyka utknęła na Rosalind i plikach .txt."
   ▼
=== BLOK II: CO ZBUDOWAŁEM? (Demo produktu – 5 kliknięć) ===
[4. Karuzela 5 ekranów: OAuth -> Edytor -> Błędny Run -> Udany Submit -> Profil/Heatmapa]
   │  Kotwica (ścieżka użytkownika): "Loguję się (1) -> Piszę kod (2) -> Mylę się w Run (3) -> Zaliczam w Submit (4) -> Buduję Streak w profilu (5)."
   ▼
=== BLOK III: Z CZEGO I JAK TO STOI? (Architektura: od kodu do klastra) ===
[5. Stos technologiczny + Vertical Slice Architecture]
   │  Kotwica: "Svelte 5 na froncie, FastAPI w 5 autonomicznych modułach domenowych i Judge0 z boku."
   ▼
[6. Architektura K8s i 3 strefy sieciowe (Ingress -> App -> Izolowany Judge0)]
   │  Kotwica: "Obcy kod jest groźny -> dzielimy klaster K8s na 3 strefy (Ingress SPA, Backend+DB, odcięty NetworkPolicy Sandbox z Redisem i Workerami)."
   ▼
=== BLOK IV: NAJTRUDNIEJSZY PROBLEM INŻYNIERSKI (Od zderzenia do kodu) ===
[7. Zderzenie (?!): Obiektowe IDE vs surowy stdin/stdout Judge0]
   │  Kotwica: "Użytkownik chce klasy Solution, return i print() do debugu, a czysty Judge0 zna tylko stdin i jeden strumień stdout."
   ▼
[8. Przepływ żądań (Sequence Diagram: UI -> FastAPI -> Judge0 + Scenariusz A/B)]
   │  Kotwica: "Jak to spinamy w czasie? Paczka N testów idzie do Judge0, wraca webhookami: N/N daje Streak (A), błąd na k-tym teście daje diagnostykę (B)."
   ▼
[9. Kod wrappera (Porównanie: Kod użytkownika vs Skrypt po opakowaniu)]
   │  Kotwica: "Jak to działa pod maską w Pythonie? Wstrzykujemy typy, redirect_stdout(sys.stderr) oddziela printy użytkownika od JSON-a z return."
   ▼
[10. Podziękowanie (algobio.io)]


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
