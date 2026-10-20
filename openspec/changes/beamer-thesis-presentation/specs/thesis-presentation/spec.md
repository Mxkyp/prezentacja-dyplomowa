## Purpose

Definiuje wymagania wizualne, strukturalne, merytoryczne oraz językowe dla prezentacji w LaTeX Beamer referującej pracę inżynierską „AlgoBio – wysoce skalowalna platforma do nauki algorytmów bioinformatyki” podczas obrony dyplomowej na Wydziale FTIMS Politechniki Łódzkiej.

## ADDED Requirements

### Requirement: Stylistyka Warsaw z czerwoną paletą kolorystyczną (#8B0002)
Prezentacja SHALL wykorzystywać klasyczny motyw `Warsaw` pakietu LaTeX Beamer bez modyfikacji jego układu strukturalnego, przy czym główny kolor struktury (domyślnie niebieski) MUST zostać zastąpiony kolorem `#8B0002`.

#### Scenario: Kompilacja motywu i weryfikacja koloru
- **WHEN** plik źródłowy LaTeX jest kompilowany do formatu PDF
- **THEN** dokument używa motywu `\usetheme{Warsaw}` oraz definiuje kolor główny odpowiadający wartości heksadecymalnej `#8B0002` dla elementów strukturalnych Beamer

### Requirement: Struktura slajdów dopasowana do czasu wystąpienia (7–8 minut)
Prezentacja SHALL składać się z 7 do 8 slajdów tworzących spójną narrację na 7–8 minut wystąpienia przed komisją nieznającą wcześniej projektu.

#### Scenario: Weryfikacja liczby slajdów i danych tytułowych
- **WHEN** wygenerowany zostaje dokument PDF prezentacji
- **THEN** dokument liczy od 7 do 8 ramek (`frame`), a slajd tytułowy zawiera tytuł „AlgoBio – wysoce skalowalna platforma do nauki algorytmów bioinformatyki”, autora (Mikołaj Pawłoś), promotora (dr inż. Mateusz Smoliński) oraz jednostkę (Wydział Fizyki Technicznej, Informatyki i Matematyki Stosowanej, Politechnika Łódzka)

### Requirement: Motywacja wyboru tematu w oparciu o istniejące platformy
Prezentacja SHALL uzasadniać wybór tematu poprzez zestawienie luki w edukacji bioinformatycznej z mnogością nowoczesnych platform w innych domenach IT.

#### Scenario: Przedstawienie luki rynkowej i ograniczeń istniejących rozwiązań
- **WHEN** prezentowana jest sekcja motywacji
- **THEN** slajd przywołuje nowoczesne platformy z innych dziedzin (**LeetCode**, **NeetCode**, **HackerRank**, **getcracked.io**) oraz kontrastuje ich interaktywny model z ograniczeniami platformy **Rosalind** (pobieranie plików tekstowych i lokalne uruchamianie kodu bez edytora w przeglądarce)

### Requirement: Prezentacja założeń projektu, strategii rozwiązania i rezultatu
Prezentacja SHALL wprowadzać komisję w koncepcję systemu AlgoBio, omawiać strategię architektoniczną oraz prezentować końcowy rezultat implementacji bez odwoływania się do metodyki SDD.

#### Scenario: Omówienie architektury i osiągniętego rezultatu
- **WHEN** prezentowane są slajdy dotyczące projektu, strategii i rezultatu
- **THEN** uwzględniają one podział na frontend (Svelte 5, TypeScript, TailwindCSS, CodeMirror), backend w architekturze Vertical Slice Architecture (FastAPI, SQLAlchemy, PostgreSQL) i izolowany silnik Judge0, a także zrealizowane funkcjonalności (tryby `Run` i `Submit`, Google OAuth2, system gamifikacji ze streakiem i mapą aktywności), nie zawierając żadnych wzmianek o Spec-Driven Development (SDD)

### Requirement: Wnioski i omówienie problemu wrappowania kodu użytkownika
Sekcja wniosków i spostrzeżeń SHALL oceniać stopień realizacji celu inżynierskiego oraz omawiać napotkane trudności techniczne i sposoby ich rozwiązania, ze szczególnym uwzględnieniem mechanizmu opakowywania (wrappowania) kodu użytkownika.

#### Scenario: Wyjaśnienie mechanizmu wrappowania kodu i pozostałych wyzwań
- **WHEN** prezentowana jest sekcja wniosków i trudności inżynierskich
- **THEN** jako główne wyzwanie techniczne omówiony zostaje proces automatycznego opakowywania kodu użytkownika w niezbędne klasy uruchomieniowe, struktury danych oraz importy przed egzekucją w Judge0, uzupełniony o asynchroniczną obsługę webhooków oraz testy integracyjne z użyciem Testcontainers

### Requirement: Estetyka oraz poprawność ortograficzna i typograficzna
Treść wszystkich slajdów MUST być wolna od błędów ortograficznych, gramatycznych, interpunkcyjnych oraz literówek w języku polskim, a układ treści na slajdach SHALL zapobiegać przepełnieniom (`overfull \hbox`/`\vbox`).

#### Scenario: Kontrola językowa i wizualna slajdów
- **WHEN** prezentacja zostaje skompilowana
- **THEN** wszystkie teksty stosują poprawną polską ortografię i typografię (w tym poprawny zapis skrótu „dr inż.” bez kropki po „dr”), a kompilacja LaTeX nie generuje błędów składniowych ani uciętych elementów na slajdach
