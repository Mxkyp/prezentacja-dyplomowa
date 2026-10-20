## Context

Tworzymy prezentację obronną pracy inżynierskiej w systemie LaTeX Beamer (motywację i zakres opisano w `proposal.md`, a wymagania formalne w `specs/thesis-presentation/spec.md`). Prezentacja musi zachować klasyczny układ motywu `Warsaw`, zmienić kolor główny na `#8B0002`, zmieścić się w 8 slajdach (~7,5 minuty wystąpienia) oraz w klarowny sposób przedstawić architekturę i główne wyzwanie inżynierskie projektu **AlgoBio** komisji nieznającej wcześniej pracy.

## Goals / Non-Goals

**Goals:**
- Przygotowanie samodzielnego, czystego pliku `presentation.tex` kompilującego się bezbłędnie przez `pdflatex` (z obsługą języka polskiego `babel`/`polski`, `utf8` i `T1`).
- Zastosowanie motywu `Warsaw` z kolorem strukturalnym `#8B0002` bez ingerencji w układ nagłówka/stopki motywu.
- Wykorzystanie wektorowych schematów `TikZ` oraz czytelnych bloków Beamer (`block`, `alertblock`, `exampleblock`, układ dwukolumnowy `columns`) do wizualizacji architektury i mechanizmu wrappowania kodu użytkownika.
- Zapewnienie braku błędów przepełnienia (`overfull \hbox`/`\vbox`) oraz 100% poprawności ortograficznej i typograficznej w języku polskim.

**Non-Goals:**
- Zastępowanie szablonu `Warsaw` innym motywem lub ręczne przebudowywanie jego pasków nawigacyjnych (`headline`/`footline`).
- Umieszczanie długich ścian tekstu lub pełnych plików źródłowych na slajdach.
- Wspominanie o metodyce SDD (Spec-Driven Development).

## Decisions

### 1. Konfiguracja kolorystyki w motywie `Warsaw`
- **Decyzja:** Użycie `\usetheme{Warsaw}` w połączeniu z definicją koloru `\definecolor{MainRed}{HTML}{8B0002}` oraz przypisaniem `\usecolortheme[named=MainRed]{structure}`.
- **Uzasadnienie:** W Beamerze motyw `Warsaw` ładuje wewnętrznie motyw kolorystyczny `orchid` oraz `whale`, które bazują na kolorze `structure` (wykorzystując jego odcienie m.in. `structure.fg!85!black` i `structure.fg!50!black` dla palet `palette primary` – `palette quaternary`). Nadpisanie koloru `structure` na `#8B0002` automatycznie i spójnie przelicza wszystkie gradienty, cienie i belki w motywie `Warsaw` z niebieskiego na czerwień PŁ, zachowując 100% oryginalnego stylu `Warsaw`.
- **Alternatywy:** Ręczne nadpisywanie każdej z palet `palette primary`..`quaternary` osobno — odrzucone, ponieważ `\usecolortheme[named=MainRed]{structure}` robi to natywnie i zachowuje fabryczne proporcje cieniowania `Warsaw`.

### 2. Proporcje ekranu 16:9 (`aspectratio=169`)
- **Decyzja:** Ustawienie `\documentclass[10pt,aspectratio=169]{beamer}`.
- **Uzasadnienie:** Motyw `Warsaw` posiada rozbudowany nagłówek z sekcjami oraz stopkę. W proporcjach 16:9 zyskujemy szerokość na układ dwukolumnowy (np. porównanie platform po lewej, tabela/diagram po prawej) bez ryzyka przepełnienia w pionie (`overfull \vbox`).

### 3. Wizualizacja problemu wrappowania kodu (Slajd 5 i 7)
- **Decyzja:** Przedstawienie procesu wrappowania kodu użytkownika za pomocą czytelnego diagramu przepływu `TikZ` oraz zwięzłego zestawienia „Co pisze użytkownik” vs „Co trafia do Judge0”.
- **Uzasadnienie:** Komisja nie zna kodu AlgoBio. Zamiast wklejać kilkadziesiąt linii Pythona, schemat blokowy + krótki przykład pokaże od razu istotę problemu: użytkownik implementuje jedynie metodę domenową, natomiast backend automatycznie dołącza niezbędne importy (`typing`, struktury danych), klasy pomocnicze, parser wejścia ze `stdin` oraz punkt wejścia serializujący wynik na `stdout`.

### 4. Podział na sekcje w nagłówku `Warsaw`
- **Decyzja:** Zdefiniowanie 5 zwięzłych sekcji (`\section{...}`), które odpowiadają 5 punktom wymaganych zagadnień obrony:
  1. `Motywacja` (Slajd 2)
  2. `Projekt AlgoBio` (Slajd 3)
  3. `Strategia i architektura` (Slajdy 4–5)
  4. `Rezultat implementacji` (Slajd 6)
  5. `Wnioski i wyzwania` (Slajdy 7–8)
- **Uzasadnienie:** Motyw `Warsaw` wyświetla wszystkie sekcje w górnym pasku. Pięć krótkich nazw sekcji idealnie mieści się w nagłówku i pozwala komisji na bieżąco śledzić realizację wymaganych punktów prezentacji.

## Risks / Trade-offs

- **[Ryzyko] Przepełnienie nagłówka lub ramek w motywie `Warsaw`** → **Mitygacja:** Stosowanie krótkich tytułów sekcji, czcionki bazowej `10pt`, proporcji `169` oraz weryfikacja logów kompilacji `pdflatex` pod kątem `Overfull \vbox` i `Overfull \hbox`.
- **[Ryzyko] Brak zewnętrznych plików graficznych podczas kompilacji** → **Mitygacja:** Wykonanie wszystkich schematów architektonicznych natywnie w `TikZ` wewnątrz pliku `.tex`, dzięki czemu prezentacja jest w pełni samowystarczalna i wektorowa.
