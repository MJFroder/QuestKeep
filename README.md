# QuestKeep

Darmowy, niekomercyjny kalendarz rozgrywek planszowych: w co, kiedy i w ile osób się grało. Działa na telefonie jak aplikacja (PWA), także bez internetu.

- kalendarz miesięczny z kolorowymi oznaczeniami gier,
- zapis rozgrywki: gra, data, liczba graczy, kto grał, zwycięzca, czas, notatki,
- podpowiedzi z bazy **31 757 gier** z rankingu BoardGameGeek,
- **własne nazwy gier**: możesz dopisać grze z BGG swoją nazwę (np. polski tytuł). Aplikacja ją zapamięta i będzie jej używać w kalendarzu, statystykach i wyszukiwaniu,
- statystyki: najczęściej grane gry, aktywność w miesiącach, liczba osób przy stole, zwycięzcy, postęp w BGG Top 100,
- historia z wyszukiwarką oraz kopia zapasowa danych do pliku.

## Zanim opublikujesz: logo „Powered by BGG”

Warunki BoardGameGeek wymagają, żeby publicznie dostępna aplikacja korzystająca z ich danych pokazywała logo **„Powered by BGG”** z linkiem do BoardGameGeek.

1. Wejdź na stronę z logotypami BGG (link „Powered by BGG Logos” znajdziesz w *XML API Terms of Use* na boardgamegeek.com).
2. Pobierz wybrane logo w formacie PNG.
3. Zapisz je jako `icons/powered-by-bgg.png`.

Aplikacja pokazuje to logo w stopce, z linkiem do BoardGameGeek. Dopóki pliku nie ma, w tym miejscu wyświetla się napis „Powered by BGG”.

## Publikacja na GitHub Pages

1. Załóż na GitHubie nowe, **publiczne** repozytorium, np. `planszowki`.
2. Wgraj do niego wszystkie pliki z tego folderu (*Add file → Upload files*), razem z folderem `icons` i plikiem `.nojekyll`.
3. Wejdź w *Settings → Pages*. W polu *Source* wybierz *Deploy from a branch*, gałąź `main`, folder `/ (root)` i kliknij *Save*.
4. Po minucie lub dwóch aplikacja będzie dostępna pod adresem
   `https://TWOJA-NAZWA.github.io/planszowki/`.

## Plik APK na Androida (budowany automatycznie)

W repozytorium jest projekt aplikacji na Androida (folder `android`) i automat GitHub Actions (`.github/workflows/android.yml`). Po każdej zmianie w repozytorium GitHub sam buduje plik **QuestKeep.apk**. Plik jest zbudowany na **Androida 17 (API 37)** i działa na telefonach z Androidem 7 lub nowszym.

1. Upewnij się, że w repozytorium jest plik `.github/workflows/android.yml`. Folder `.github` jest ukryty i przy przeciąganiu plików czasem się pomija. Wtedy utwórz go ręcznie: *Add file → Create new file*, nazwa `.github/workflows/android.yml`, i wklej zawartość.
2. Zakładka **Actions**: budowanie trwa około 5 minut. Zielony znaczek oznacza gotowe.
3. Zakładka **Releases** (po prawej na stronie repozytorium) albo adres `https://github.com/TWOJA-NAZWA/NAZWA-REPO/releases/latest`. Na telefonie pobierz stamtąd **QuestKeep.apk**.
4. Otwórz pobrany plik. Android poprosi o zgodę na instalowanie aplikacji z tego źródła (przeglądarki lub menedżera plików). Zezwól.
5. Google Play Protect może zaproponować sprawdzenie aplikacji od nieznanego twórcy. To normalne przy aplikacjach spoza Sklepu Play: wybierz sprawdzenie albo „Zainstaluj mimo to”.

Kolejne wersje instalują się na poprzedniej, a dane zostają.

**Klucz podpisu:** plik `android/app/release.keystore` podpisuje aplikację i musi zostać ten sam, inaczej telefon nie zainstaluje aktualizacji. Do prywatnego, hobbystycznego projektu to wystarczy. Jeśli kiedyś zechcesz publikować w Sklepie Play, wygeneruj nowy klucz i trzymaj hasła w *Settings → Secrets* (`KEYSTORE_PASSWORD`, `KEY_PASSWORD`, `KEY_ALIAS`).

## Instalacja jako aplikacja z przeglądarki (bez APK)

**Android (Chrome):** otwórz link do strony, stuknij menu ⋮ i wybierz *Zainstaluj aplikację*.

**iPhone (Safari):** otwórz link, stuknij *Udostępnij* i wybierz *Do ekranu początkowego*.

## Gdzie są dane

Każda osoba ma własny dziennik, zapisany tylko w pamięci przeglądarki na swoim telefonie. Nic nie jest wysyłane na serwer.

- Wyczyszczenie danych przeglądarki albo odinstalowanie aplikacji usuwa zapisane rozgrywki.
- Kopię zrobisz w zakładce **Historia → Zapisz kopię danych** (plik `.json`). Ten sam plik wczytasz przyciskiem **Wczytaj kopię**, np. na nowym telefonie. Kopia obejmuje też własne nazwy gier.

## Aktualizacja

Po zmianie plików podnieś numer wersji w `sw.js` (`const CACHE = "bgc-v3"` → `bgc-v4`), żeby telefony pobrały nową wersję.

## Dane i licencja

- **Dane gier** (`games.js`): pochodzą z BoardGameGeek (boardgamegeek.com), z pliku `boardgames_ranks.csv` udostępnianego przez BGG (listopad 2026). Obejmują gry podstawowe z miejscem w rankingu: nazwę, rok wydania i miejsce w rankingu, **bez zmian**. Dane są używane wyłącznie niekomercyjnie, zgodnie z *BGG XML API Terms of Use*. Powered by BGG.
- Aplikacja nie jest powiązana z BoardGameGeek.
- **Aplikacja musi pozostać niekomercyjna:** bez reklam, opłat i sprzedaży. Do zastosowań komercyjnych BGG wymaga osobnej licencji.
- **Kod aplikacji:** licencja MIT (plik `LICENSE`). Nie obejmuje ona danych z BGG.
