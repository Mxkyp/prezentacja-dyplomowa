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
     - *Mnogość platform w innych domenach IT*: Na rynku z powodzeniem funkcjonuje wiele nowoczesnych, interaktywnych platform szkoleniowych dla innych dziedzin informatyki – np. **LeetCode**, **NeetCode**, **HackerRank** (algorytmika ogólna i struktury danych) czy **getcracked.io** (niskopoziomowy C++ i systemy). Oferują one świetny UX (edytor w przeglądarce, natychmiastowa informacja zwrotna, grywalizacja), ale pomijają domenę bioinformatyki.
     - *Rosalind (bioinformatyka)*: Posiada bogatą bazę zadań bioinformatycznych, ale opiera się na przestarzałym modelu pracy (pobieranie plików `.txt`, lokalne uruchamianie skryptu w 5-minutowym oknie czasowym, wklejanie wyniku tekstowego – brak edytora w chmurze oraz automatycznej weryfikacji samego kodu i przypadków brzegowych).
  3. **Zreferowanie projektu inżynierskiego (Slajd 3):** Wprowadzenie komisji w koncepcję platformy AlgoBio (aktorzy: Gość, Użytkownik, Administrator; interaktywny edytor w przeglądarce, dwa tryby uruchamiania `Run` i `Submit`, profil użytkownika ze statystykami i gamifikacją).
  4. **Strategia rozwiązania i podejście inżynierskie (Slajdy 4–5):**
     - Architektura systemu: Frontend (Svelte 5, TypeScript, TailwindCSS v4, CodeMirror 6) + Backend (Python 3.14, FastAPI, SQLAlchemy 2.0, Alembic, PostgreSQL) + Sandbox wykonawczy (Judge0).
     - Podział backendu w oparciu o **Vertical Slice Architecture (VSA)** (`auth`, `problem`, `submission`, `judge0`, `user`).
     - Testy integracyjne z wykorzystaniem rzeczywistej bazy danych w **Testcontainers**.
     - Bezpieczna izolacja wykonania niezaufanego kodu przez **Judge0** i mechanizm opakowywania (wrappowania) kodu użytkownika w niezbędne klasy, struktury oraz importy przed egzekucją.
  5. **Rezultat i implementacja (Slajd 6):** Działająca platforma webowa (SPA), Google OAuth2 + JWT, edytor z rozszerzalnym panelem wyników testów, system gamifikacji (dzienne serie *streaks*, mapa aktywności *heatmap*).
  6. **Wnioski, trudności i sposoby ich rozwiązania (Slajd 7):**
     - *Główne wyzwanie inżynierskie – wrappowanie kodu użytkownika:* Konieczność odciążenia użytkownika z pisania kodu szablonowego (boilerplate), obsługi wejścia/wyjścia (`stdin`/`stdout`) oraz ręcznego importowania bibliotek. Rozwiązano to poprzez automatyczne opakowywanie (wrapping) przesłanej funkcji użytkownika w dedykowane klasy uruchomieniowe, struktury pomocnicze oraz niezbędne importy przed wysłaniem paczki wykonawczej do silnika Judge0.
     - *Wyzwanie 2 – asynchroniczna ewaluacja:* Zastąpienie blokującego odpytywania (polling) silnika Judge0 asynchronicznym przepływem opartym o webhooki (`PUT /judge0/submit/{id}`).
     - *Wyzwanie 3 – wiarygodność testów integracyjnych:* Uniknięcie złudnej pewności z nadmiernego mockowania bazy poprzez testy na żywym kontenerze PostgreSQL (Testcontainers).
  7. **Podsumowanie i kierunki rozwoju (Slajd 8):** Potwierdzenie osiągnięcia celu inżynierskiego oraz dalsze plany (pełna asynchroniczność bazy, kolejni dostawcy OAuth2 jak ORCID/GitHub).

## Capabilities

### New Capabilities
- `thesis-presentation`: Struktura, stylistyka (`Warsaw` + `#8B0002`), zawartość merytoryczna 8 slajdów oraz poprawność ortograficzna i typograficzna prezentacji obronnej pracy inżynierskiej AlgoBio.

### Modified Capabilities
<!-- Brak istniejących specyfikacji -->

## Impact

- Nowy zestaw plików źródłowych prezentacji LaTeX Beamer (`.tex`) oraz skompilowany plik `.pdf` w repozytorium.
