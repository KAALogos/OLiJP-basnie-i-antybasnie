# Testy akceptacyjne UX 7 — 15 października 2026

Scenariusze przeprowadzono w Chromium 144 z użyciem Playwright na lokalnych HTML, w tym pełny obieg eksport/import JSON między dwoma niezależnymi widokami uczennicy i nauczyciela.

| Scenariusz | Wynik | Co zweryfikowano |
|---|---|---|
| 1. Pierwsze uruchomienie i ćwiczenie | PASS | Pięć sekcji menu, problem–przykład–działanie, niewyświetlanie gotowej tezy przed próbą, zapis odpowiedzi |
| 2. Przerwanie i wznowienie | PASS w symulacji | Serializacja danych, ponowne otwarcie w nowym widoku i przycisk „Wróć do szkicu” |
| 3. Przekazanie pracy | PASS | Oznaczenie jako gotowa, osobny pobrany plik z jedną pracą, zgodność identyfikatora i statusu |
| 4. Ocena nauczyciela | PASS | Import pracy, jawny wybór statusu, wymagane informacje zwrotne, eksport oceny; brak automatycznego przypisywania oceny |
| 5. Poprawka i porównanie | PASS | Wczytanie informacji zwrotnej, status „Do poprawy”, zachowanie pierwotnego tekstu, edycja, porównanie, kolejna ocena |
| Plik nieprawidłowy | PASS | Jasny komunikat błędu; bez zmiany istniejących prac i ocen |
| Telefon i skupienie | PASS | Szeroki edytor 390 px, brak poziomego przewijania, kontekst schowany na wąskim ekranie, tryb skupienia |
| Składnia JavaScript | PASS | Oba pliki przechodzą `node --check`, bez wyjątków podczas testowanych scenariuszy |

**Ograniczenie testów:** polityka środowiska uniemożliwiła bezpośrednią nawigację przeglądarki do lokalnego `file://` lub serwera `localhost`. Testy wykonały HTML w Chromium przy emulacji pamięci przeglądarki (`localStorage`) i przekazaniu jej stanu do nowego widoku. Zachowanie natywnego `localStorage` po fizycznym zamknięciu Chrome wymaga testu na docelowym komputerze. Nie należy traktować tego jednego aspektu jako potwierdzonego w docelowym środowisku.

**Dane merytoryczne:** przepisano istniejące HTML bez zamiany tablicy `DATA` na inny korpus; nie przeprowadzono osobnego pełnego audytu 90 kart źródłowych, ponieważ obecny HTML jest nadal częściowym MVP.
