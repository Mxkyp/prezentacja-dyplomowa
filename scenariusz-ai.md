# Scenariusz prezentacji obrony inżynierskiej – AlgoBio (limit: 8 min)

---

## Część 1: Heurystyczna ściągawka pamięciowa (Mapa myśli i przejść)

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
```

### Szybka ściąga slajd po slajdzie (1–2 zdania wodzące + licznik kliknięć)

1. **Tytułowy** *(1 klik)*
   * *Myśl przewodnia:* Powitanie Komisji, przedstawienie siebie, tematu pracy i promotora (dr inż. Mateusz Smoliński).
2. **Paradygmat „LeetCode”** *(3 stany na 1 slajdzie: `1/3` -> `2/3` -> `3/3`)*
   * *Myśl przewodnia:* Nowoczesna nauka algorytmiki nie wymaga parsowania plików – dostajemy obiektowy szablon z typem `FastqRead` `(1/3)`, testujemy przykłady przyciskiem **Run** `(2/3)` i wysyłamy pełną paczkę testów przez **Submit** `(3/3)`.
3. **Wyspecjalizowane odpowiedniki LeetCode** *(1 klik)*
   * *Myśl przewodnia:* Od finansów (*QuantGuide*) po FPGA (*HDLBits*) każda dziedzina ma taki interaktywny sandbox, natomiast w bioinformatyce wciąż dominuje archaiczny *Rosalind* oparty na ręcznym pobieraniu plików `.txt` na dysk – tę lukę wypełnia **AlgoBio**.
4. **Rezultat pracy – zrealizowana platforma AlgoBio** *(5 stanów na 1 slajdzie: `1/5` -> `5/5`)*
   * *Myśl przewodnia (idziesz dokładnie ścieżką użytkownika):*
     * `1/5`: Logowanie bezhasłowe OAuth 2.0 (Google / GitHub).
     * `2/5`: Dwuokienkowy widok zadania z edytorem CodeMirror 6 i testami.
     * `3/5`: Tryb **Run** – natychmiastowa diagnostyka błędu (*Expected* vs *Actual*).
     * `4/5`: Tryb **Submit** – zaliczenie wszystkich testów i podbicie serii (*Streak*).
     * `5/5`: Profil użytkownika ze statystykami i roczną mapą aktywności (jak na GitHubie).
5. **Strategia rozwiązania i architektura systemu** *(1 klik)*
   * *Myśl przewodnia:* Lekki frontend SPA w **Svelte 5** oraz backend w **Pythonie 3.14 / FastAPI** podzielony według **Vertical Slice Architecture** na 5 niezależnych modułów domenowych (`auth`, `problem`, `submission`, `judge0`, `user`), z bazą PostgreSQL i silnikiem Judge0.
6. **Architektura wdrożeniowa Kubernetes i separacja sieciowa** *(1 klik)*
   * *Myśl przewodnia:* Ze względów bezpieczeństwa klaster K8s podzielono na 3 strefy: **Ingress** (serwujący statyczny bundle SPA i routujący `/api/*`), **Strefę Aplikacyjną** (repliki FastAPI + PostgreSQL) oraz **Strefę Izolowaną Sandboxa** (`NetworkPolicy`), gdzie API Judge0, kolejka Redis i Workery wykonujące kod są odcięte od głównej bazy danych.
7. **Wyzwanie: Obiektowe IDE a surowy model I/O Judge0** *(1 klik)*
   * *Myśl przewodnia:* Zderzenie dwóch światów (`?!`): użytkownik w IDE pisze obiektową metodę z `return` i używa `print()` do debugowania, podczas gdy czysty silnik Judge0 operuje wyłącznie na surowych strumieniach `stdin`/`stdout`, przez co zwykły `print("dbg")` miesza się z wynikiem algorytmu.
8. **Rozwiązanie: Przepływ żądań i wielotestowa ewaluacja** *(1 klik)*
   * *Myśl przewodnia:* Backend przyjmuje kod (`POST /submit`), opakowuje go i wysyła paczkę $N$ testów do Judge0, odbierając wyniki asynchronicznie przez webhooki (`PUT`): zaliczenie $N/N$ testów aktualizuje *Streak* (**Scenariusz A**), a błąd na $k$-tym teście zwraca dokładny diff i logi z `print()` (**Scenariusz B**).
9. **Rozwiązanie: Mechanizm opakowywania (wrappowania) kodu** *(1 klik)*
   * *Myśl przewodnia:* Backend dynamicznie skleja kod użytkownika z importem typów (`FastqRead`) i runnerem, który za pomocą `with redirect_stdout(sys.stderr):` przekierowuje wszystkie `print()` użytkownika na `stderr` (jako logi debugowania), a wartość z `return` serializuje do JSON-a na czyste `stdout`.
10. **Zakończenie** *(1 klik)*
    * *Myśl przewodnia:* Podsumowanie w jednym zdaniu, podziękowanie za uwagę i zaproszenie na `algobio.io`.

---

## Część 2: Pełny scenariusz wypowiedzi z budżetem czasowym (~7 min 30 s)

### 1. Wstęp i Motywacja (~1:45)

* **Slajd 1 – Tytułowy (~0:15)**
  > „Dzień dobry Państwu. Nazywam się Mikołaj Pawłoś i mam przyjemność zaprezentować wyniki mojej pracy inżynierskiej pod tytułem *AlgoBio – wysoce skalowalna platforma do nauki algorytmów bioinformatyki*, zrealizowanej pod opieką pana doktora inżyniera Mateusza Smolińskiego.”

* **Slajd 2 – Paradygmat „LeetCode” (kroki `1/3` -> `2/3` -> `3/3`) (~0:50)**
  > * **(Krok 1/3):** „Współczesna nauka algorytmiki w przeglądarce opiera się na paradygmacie spopularyzowanym przez platformę LeetCode. Użytkownik otrzymuje ustrukturyzowaną treść zadania `(1)` oraz edytor kodu `(2)` z gotową sygnaturą metody i typami domenowymi – tutaj na przykładzie odczytu sekwencji DNA `FastqRead`.”
  > * **(Krok 2/3 – klik):** „Nie musi pisać kodu wczytującego pliki czy parsującego standardowe wejście. Implementuje wyłącznie logikę biznesową, klika **Run** i w panelu `(3)` natychmiast weryfikuje działanie na przykładowych przypadkach testowych.”
  > * **(Krok 3/3 – klik):** „Po kliknięciu **Submit** kod przechodzi przez pełny zestaw np. 50 ukrytych testów w izolowanym środowisku, zwracając werdykt *Accepted*, metryki czasu i pamięci oraz budując codzienną serię aktywności (*Streak*).”

* **Slajd 3 – Wyspecjalizowane odpowiedniki LeetCode (~0:40)**
  > „Ten model okazał się tak skuteczny, że wokół niego wyrosły wyspecjalizowane platformy dla konkretnych branż: od finansów ilościowych (*QuantGuide*), przez *Machine Learning* i *SQL*, aż po programowanie układów FPGA (*HDLBits*) czy *DevOps*.
  > Kiedy jednak spojrzymy na **bioinformatykę**, napotykamy lukę. Najpopularniejsza platforma – *Rosalind* – powstała kilkanaście lat temu i opiera się na ręcznym pobieraniu plików tekstowych na dysk, uruchamianiu skryptu lokalnie i wklejaniu wyniku w formularz, z 5-minutowym limitem czasu i brakiem ochrony przed oszustwami. To właśnie zmotywowało mnie do stworzenia **AlgoBio**.”

---

### 2. Rezultat pracy – zrealizowana platforma AlgoBio (~1:15)

* **Slajd 4 – Karuzela 5 zrzutów ekranu (`1/5` -> `5/5`) (~15 sekund na ekran)**
  > * **(1/5 OAuth):** „Przejdźmy do zrealizowanego systemu. Platforma zapewnia bezpieczne, bezhasłowe uwierzytelnianie w standardzie OAuth 2.0 przez konta Google oraz GitHub.”
  > * **(2/5 Widok problemu):** „Sercem aplikacji jest dwuokienkowy interfejs problemu. Po lewej stronie znajduje się opis biologiczny i specyfikacja algorytmiczna, po prawej – edytor *CodeMirror 6* ze wsparciem składni Pythona oraz panel przypadków testowych.”
  > * **(3/5 Tryb Run – błąd):** „W trybie *Run* użytkownik otrzymuje błyskawiczną diagnostykę. W przypadku błędu dokładnie widzi, dla jakiego wejścia algorytm zwrócił niepoprawny wynik (*Expected* kontra *Actual*).”
  > * **(4/5 Tryb Submit – sukces):** „Z kolei w trybie *Submit*, po przejściu pełnej paczki testów, użytkownik otrzymuje potwierdzenie zaliczenia zadania oraz modal podsumowujący jego serię (*Streak*).”
  > * **(5/5 Profil i Heatmap):** „Długofalowe zaangażowanie wspiera profil użytkownika ze statystykami oraz roczną mapą aktywności wzorowaną na GitHubie.”

---

### 3. Strategia rozwiązania i architektura (~1:45)

* **Slajd 5 – Stos technologiczny i architektura logiczna (~0:45)**
  > „Od strony projektowej zależało mi na niskim narzucie utrzymaniowym przy wysokiej wydajności. Warstwa kliencka to *Single Page Application* w **Svelte 5** i **TypeScript**.
  > Backend zrealizowałem w **Pythonie 3.14** oraz asynchronicznym frameworku **FastAPI**, stosując architekturę **Vertical Slice** – kod nie jest podzielony na sztuczne warstwy techniczne, lecz na 5 autonomicznych modułów domenowych (`auth`, `problem`, `submission`, `judge0` oraz `user`). Za wykonywanie niezaufanego kodu odpowiada otwartoźródłowy silnik **Judge0**.”

* **Slajd 6 – Architektura wdrożeniowa Kubernetes i separacja sieciowa (~1:00)**
  > „Ponieważ system wykonuje dowolny kod nadesłany przez użytkowników, kluczowym aspektem inżynierskim była architektura wdrożeniowa w klastrze **Kubernetes** i separacja sieciowa.
  > * Ruch HTTPS trafia na **Ingress Controller**, który serwuje statyczny pakiet SPA dla przeglądarki użytkownika, a zapytania `/api/*` kieruje do **Strefy Aplikacyjnej**. Tam działają skalowalne repliki backendu FastAPI oraz baza danych PostgreSQL.
  > * Sam silnik wykonawczy wydzieliłem do osobnej **Strefy Izolowanej Sandboxa** w dedykowanym *Namespace* obłożonym politykami **NetworkPolicy**.
  > * Jedynym punktem styku między strefami jest wewnętrzny kanał komunikacji z API Judge0 (zlecenie zadania i odbiór webhooka). Wewnątrz strefy sandboxa zadania trafiają przez kolejkę **Redis** do skalowalnych **Workerów Judge0**, które są całkowicie odcięte od głównej bazy danych AlgoBio.”

---

### 4. Wnioski i wyzwania – Obiektowe IDE a surowy Judge0 (~2:30)

* **Slajd 7 – Zderzenie oczekiwań: Obiektowe IDE vs czysty Judge0 (~0:50)**
  > „Najciekawszym wyzwaniem inżynierskim podczas realizacji pracy było pogodzenie nowoczesnego, obiektowego IDE z surowym modelem wejścia/wyjścia silnika Judge0.
  > * Z perspektywy użytkownika w AlgoBio dostarczamy kod startowy z klasą `Solution` i typami biologicznymi (jak `FastqRead`). Użytkownik oczekuje, że metoda zostanie wywołana obiektowo, instrukcja `return` posłuży do weryfikacji wyniku, a ewentualne wywołania `print()` trafią do osobnego panelu logów debugowania.
  > * Tymczasem czysty silnik Judge0 działa jak klasyczna czarna skrzynka uniksowa: przyjmuje surowy tekst na `stdin`, uruchamia kontener i zwraca wszystko, co pojawiło się na `stdout`. Sam z siebie nie potrafi zainstancjonować klasy, nie widzi wartości z `return`, a zwykły `print("dbg")` użytkownika zanieczyszcza strumień wyjściowy, uniemożliwiając ocenę.”

* **Slajd 8 – Przepływ żądań, wielotestowa ewaluacja i obsługa błędów (~0:50)**
  > „Jak zostało to rozwiązane? Spójrzmy na pełny przepływ żądań:
  > 1. Po pobraniu zadania i napisaniu kodu użytkownik wysyła go metodą `POST /submit`.
  > 2. Backend pobiera z bazy zestaw $N$ przypadków testowych, opakowuje kod użytkownika w skrypt uruchomieniowy i wysyła paczkę zadań do klastra Judge0.
  > 3. Judge0 wykonuje każdy z $N$ testów niezależnie i asynchronicznie odsyła rezultaty przez *webhooki* (`PUT /judge0/submit/{id}`).
  > * Jeśli wszystkie $N$ testów zakończy się sukcesem (**Scenariusz A**), aktualizujemy postęp użytkownika i jego *Streak*.
  > * Jeśli jednak którykolwiek test – np. $k$-ty z $N$ – zakończy się błędem (**Scenariusz B**), przechwytujemy dokładny stan tego testu i zwracamy użytkownikowi zestawienie wartości oczekiwanej, otrzymanej oraz jego własnych logów z `print()`.”

* **Slajd 9 – Mechanizm opakowywania (wrappowania) kodu (~0:50)**
  > „Techniczny sekret tego mechanizmu kryje się w dynamicznym opakowywaniu kodu przed wysyłką do Judge0.
  > * Po lewej widzimy czysty kod z edytora użytkownika – z wywołaniem `print("Debug:", ...)` oraz `return`.
  > * Po prawej widzimy kompletny skrypt generowany przez backend. Wstrzykujemy do niego definicje typów bioinformatycznych (`from algobio_types import FastqRead`), kod klasy `Solution`, a na dole doklejamy blok uruchomieniowy.
  > * Kluczowy zabieg to użycie menedżera kontekstu `with redirect_stdout(sys.stderr):` podczas wywołania metody użytkownika. Dzięki temu każdy `print()` wykonany wewnątrz algorytmu zostaje przekierowany na strumień błędów `stderr` – skąd bezpiecznie odbieramy go jako log debugowania. Natomiast właściwy wynik z instrukcji `return` jest serializowany do formatu JSON i jako jedyny trafia na czyste `stdout`, co pozwala na jednoznaczną i niezawodną weryfikację wyniku.”

---

### 5. Podsumowanie (~0:15)

* **Slajd 10 – Podziękowanie (~0:15)**
  > „W rezultacie powstała kompletna, bezpieczna i gotowa do skalowania platforma, która przenosi naukę algorytmów bioinformatycznych do nowoczesnej przeglądarki. Dziękuję serdecznie za uwagę, zapraszam na *algobio.io* i chętnie odpowiem na pytania Komisji.”
