## 1. Konfiguracja dokumentu LaTeX Beamer i motywu Warsaw

- [x] 1.1 Utworzyć plik `presentation.tex` z klasą `\documentclass[10pt,aspectratio=169]{beamer}`, obsługą języka polskiego (`babel`, `utf8`, `T1`), pakietem `tikz` oraz `listings`/`booktabs`.
- [x] 1.2 Skonfigurować motyw `\usetheme{Warsaw}` oraz kolor główny `\definecolor{MainRed}{HTML}{8B0002}` przypisany przez `\usecolortheme[named=MainRed]{structure}`.
- [x] 1.3 Skonfigurować metadane slajdu tytułowego: tytuł (*AlgoBio – wysoce skalowalna platforma do nauki algorytmów bioinformatyki*), autor (*Mikołaj Pawłoś*), promotor (*dr inż. Mateusz Smoliński*), jednostka (*Wydział Fizyki Technicznej, Informatyki i Matematyki Stosowanej, Politechnika Łódzka*).

## 2. Opracowanie merytoryczne slajdów (1–8)

- [x] 2.1 Zaimplementować Slajd 1 (Tytułowy) oraz Slajd 2 (Sekcja 1: *Motywacja*) – zestawienie mnogości platform w innych domenach (**LeetCode**, **NeetCode**, **HackerRank**, **getcracked.io**) z ograniczeniami platformy **Rosalind** w bioinformatyce.
- [x] 2.2 Zaimplementować Slajd 3 (Sekcja 2: *Projekt AlgoBio*) – zreferowanie koncepcji systemu dla komisji (role użytkowników, główne funkcjonalności: interaktywny edytor, tryby `Run` i `Submit`, gamifikacja i statystyki).
- [x] 2.3 Zaimplementować Slajd 4 (Sekcja 3: *Strategia i architektura*) – stos technologiczny (Svelte 5, TypeScript, TailwindCSS, CodeMirror + FastAPI, SQLAlchemy 2.0, PostgreSQL, Judge0), podział na moduły **Vertical Slice Architecture (VSA)** oraz testy integracyjne w **Testcontainers** (bez wzmianek o SDD).
- [x] 2.4 Zaimplementować Slajd 5 (Sekcja 3: *Przepływ ewaluacji i wrappowanie kodu*) – diagram `TikZ` oraz wyjaśnienie mechanizmu automatycznego opakowywania kodu użytkownika w niezbędne klasy uruchomieniowe i importy przed egzekucją w kontenerze **Judge0**.
- [x] 2.5 Zaimplementować Slajd 6 (Sekcja 4: *Rezultat implementacji*) – prezentacja osiągniętego rezultatu (SPA, uwierzytelnianie Google OAuth2 + JWT, edytor z rozszerzalnym panelem testów, system gamifikacji: *streaks* i *heatmap*).
- [x] 2.6 Zaimplementować Slajd 7 (Sekcja 5: *Wnioski i wyzwania*) – szczegółowe omówienie głównego problemu inżynierskiego (wrappowanie kodu użytkownika w klasy i importy) oraz wyzwań związanych z asynchronicznymi webhookami Judge0 i testami w Testcontainers, wraz ze sposobem ich rozwiązania.
- [x] 2.7 Zaimplementować Slajd 8 (Sekcja 5: *Podsumowanie i rozwój*) – podsumowanie realizacji celu inżynierskiego, kierunki dalszego rozwoju oraz podziękowanie za uwagę.

## 3. Kompilacja, weryfikacja estetyczna i korekta językowa

- [ ] 3.1 Skompilować `presentation.tex` do `presentation.pdf` (dwukrotny przebieg `pdflatex` dla prawidłowego wygenerowania pasków sekcji w motywie `Warsaw`).
- [ ] 3.2 Sprawdzić log kompilacji (`presentation.log`) pod kątem błędów oraz ostrzeżeń `Overfull \hbox` / `Overfull \vbox` i w razie potrzeby skorygować odstępy lub rozmiary bloków.
- [ ] 3.3 Przeprowadzić weryfikację wizualną wygenerowanych slajdów PDF oraz pełną korektę pod kątem ortografii, interpunkcji i literówek w języku polskim.
