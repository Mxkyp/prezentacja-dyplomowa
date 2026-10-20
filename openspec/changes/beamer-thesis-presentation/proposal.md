## Why

Potrzebujemy przygotować estetyczną, wolną od błędów językowych prezentację w LaTeX Beamer na obronę pracy inżynierskiej na Wydziale FTIMS Politechniki Łódzkiej (7–8 minut, 7–8 slajdów), zakładając, że komisja egzaminacyjna nie zna wcześniej projektu **AlgoBio**.

## What Changes

- Stworzenie prezentacji LaTeX Beamer w klasycznym stylu `Warsaw` (bez modyfikacji układu motywu, jedynie ze zmianą głównego koloru struktury na `#8B0002` – czerwień PŁ).
- Opracowanie spójnej narracji na 8 slajdów (~7,5 minuty) realizującej wszystkie 5 punktów wymaganych na obronie:
  1. **Dane tytułowe:**
     - **Tytuł:** *AlgoBio – wysoce skalowalna platforma do nauki algorytmów bioinformatyki*
     - **Autor:** Mikołaj Pawłoś
     - **Promotor:** dr inż. Mateusz Smoliński
     - **Jednostka:** Wydział Fizyki Technicznej, Informatyki i Matematyki Stosowanej (FTIMS), Politechnika Łódzka
  2. **Motywacja wyboru tematu (Slajd 2):** Odniesienie do luki między istniejącymi rozwiązaniami:
     - *Rosalind*: bogata baza zadań bioinformatycznych, ale przestarzały model pracy (pobieranie plików `.txt`, lokalne uruchamianie skryptu w 5-minutowym oknie, brak weryfikacji kodu i przypadków brzegowych w chmurze).
     - *LeetCode / HackerRank*: świetny UX (edytor w przeglądarce, natychmiastowa informacja zwrotna, grywalizacja), ale brak zadań domenowych z bioinformatyki.
  3. **Zreferowanie projektu inżynierskiego (Slajd 3):** Wprowadzenie komisji w koncepcję platformy AlgoBio (aktorzy: Gość, Użytkownik, Administrator; interaktywny edytor w przeglądarce, dwa tryby uruchamiania `Run` i `Submit`, profil użytkownika ze statystykami i gamifikacją).
  4. **Strategia rozwiązania i podejście inżynierskie (Slajdy 4–5):**
     - Architektura systemu: Frontend (Svelte 5, TypeScript, TailwindCSS v4, CodeMirror 6) + Backend (Python 3.14, FastAPI, SQLAlchemy 2.0, Alembic, PostgreSQL) + Sandbox wykonawczy (Judge0).
     - Podział backendu w oparciu o **Vertical Slice Architecture (VSA)** (`auth`, `problem`, `submission`, `judge0`, `user`).
     - Podejście **Spec-Driven Development (SDD)** oraz testy integracyjne z wykorzystaniem **Testcontainers**.
     - Bezpieczna izolacja wykonania niezaufanego kodu przez **Judge0** i opakowanie kodu użytkownika w styl LeetCode (runner).
  5. **Rezultat i implementacja (Slajd 6):** Działająca platforma webowa (SPA), Google OAuth2 + JWT, edytor z rozszerzalnym panelem wyników testów, system gamifikacji (dzienne serie *streaks*, mapa aktywności *heatmap*).
  6. **Wnioski, trudności i sposoby ich rozwiązania (Slajd 7):**
     - *Wyzwanie 1:* Blokujące odpytywanie (polling) silnika Judge0 -> *Rozwiązanie:* Asynchroniczny przepływ oparty o webhooki (`PUT /judge0/submit/{id}`).
     - *Wyzwanie 2:* Surowe operacje `stdin`/`stdout` utrudniające pisanie rozwiązań -> *Rozwiązanie:* Wstrzykiwanie kodu w szablon uruchomieniowy (LeetCode-style runner).
     - *Wyzwanie 3:* Złudna pewność testów przy mockowaniu bazy danych i callbacków -> *Rozwiązanie:* Testy integracyjne na rzeczywistym kontenerze PostgreSQL (Testcontainers) i weryfikacja granic modułów VSA.
  7. **Podsumowanie i kierunki rozwoju (Slajd 8):** Potwierdzenie osiągnięcia celu inżynierskiego oraz dalsze plany (pełna asynchroniczność bazy, kolejni dostawcy OAuth2 jak ORCID/GitHub).

## Capabilities

### New Capabilities
- `thesis-presentation`: Struktura, stylistyka (`Warsaw` + `#8B0002`), zawartość merytoryczna 8 slajdów oraz poprawność ortograficzna i typograficzna prezentacji obronnej pracy inżynierskiej AlgoBio.

### Modified Capabilities
<!-- Brak istniejących specyfikacji -->

## Impact

- Nowy zestaw plików źródłowych prezentacji LaTeX Beamer (`.tex`) oraz skompilowany plik `.pdf` w repozytorium.
