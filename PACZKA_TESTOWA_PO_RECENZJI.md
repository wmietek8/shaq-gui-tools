# Paczka testowa po drugiej serii uwag z 1 listopada 2026

Kod do przeglądu jest podzielony na trzy niezależne PR-y:

1. [#18 — nasłuch wybranego programu](https://github.com/michaldziwisz/shaq-gui-tools/pull/18).
2. [#19 — radio, odsłuch i czytniki ekranu](https://github.com/michaldziwisz/shaq-gui-tools/pull/19).
3. [#20 — klient HTTP, sygnatura i ponowienia](https://github.com/michaldziwisz/shaq-gui-tools/pull/20).

Każdy PR jest oparty na `main` i został sprawdzony osobno. Ta gałąź łączy je
wyłącznie do wspólnej paczki testowej. Rozwiązania nakładających się zmian
znajdują się w commitach łączących gałęzie; nie zastępuje to osobnej oceny PR-ów
ani nie oznacza scalenia przez opiekuna projektu.

Uwzględnione zostały wszystkie punkty komentarzy z 17:39 UTC:

- pełny łańcuch przodków odtwarzacza, także przez procesy pomocnicze;
- trwałe, dostępne ostrzeżenie o błędzie zapisu historii, niezależne od
  zwykłego paska stanu, kasowane dopiero po udanym zapisie nowego wyniku;
- jednorazowe ogłoszenie błędu przez czytnik, z dostępnym oknem w razie
  niepowodzenia przekazania komunikatu; nasłuch nadal pracuje;
- wyszukiwanie DLL ZDSR w katalogu instalacji, bez wykrywania jej po nazwach
  uruchomionych procesów; przy braku instalacji pozostaje dołączona biblioteka;
- ustawiony limit 10–600 s w kliencie HTTP ShaqFileGUI, z domyślną wartością
  60 s i natychmiastowo przerywalnym oczekiwaniem;
- przywrócone wykładnicze pauzy plików z ograniczeniem 60 s oraz minimum
  30 s dla niepoprawnej odpowiedzi i HTTP 429 w ShaqGUI/ShaqCast;
- klasyfikowanie błędów przez pola wyjątku, niezależnie od treści komunikatu,
  oraz dokumentacja odpowiadająca tym zasadom.

`main` nadal wskazuje `6f42925910234fa804c192b9786201666f524c49`.
Po scaleniu pierwszego PR-a pozostałe wymagają dostosowania do nowego `main`.
Ta paczka zawiera sprawdzone wspólne rozwiązanie konfliktów, ale przyszłe
dostosowanie otwartych PR-ów nie jest oznaczone jako już wykonane.

W połączonym interfejsie źródła to wyjście, wejście, program i radio.
Katalogi tłumaczeń są łączone, zachowane są osobne zdarzenia radia i
rozpoznawania, a oba rodzaje nasłuchu korzystają z poprawionego klienta HTTP.

Wspólna weryfikacja na Windows / Python 3.11: **367 testów ShaqGUI/ShaqFileGUI**,
w tym rzeczywiste WASAPI, kontrolki wxPython, lokalny serwer radia z FFmpeg
i powiadomienia UI Automation, oraz **137 testów ShaqCast**. Jeden test
rzeczywistego Autostartu jest celowo pomijany. Ostrzeżenia dotyczą istniejącego
wywołania `locale.getdefaultlocale`, nie niepowodzeń testów.

Każdy PR sprawdzono również osobno: #18 — 85 + 69 testów, #19 — 155 + 19,
#20 — 163 + 87 (kolejno pakiety `shaq` i `shaqcast`). W każdej wersji
ShaqCast pominięty jest ten sam test tworzenia prawdziwego Autostartu.

Pełne opisy funkcji i ograniczeń:

- [Nasłuch programu](ZMIANY_PROCES.md)
- [Radio i czytniki](ZMIANY_RADIO_CZYTNIKI.md)
- [Rozpoznawanie](ZMIANY_ROZPOZNAWANIE.md)

Zachowane są nazwy `shaqgui.exe`, `shaqfilegui.exe`, `shaqcast.exe` i bazowa
wersja 0.1.9. Przed podmianą pliku należy zamknąć jego uruchomioną kopię.
Nie dołączono ustawień użytkownika, haseł, historii ani prywatnych nagrań.

Pełny odsłuch JAWS/ZDSR/Narrator oraz całonocna próba radia pozostają
niepotwierdzone; nie są oznaczone jako wykonane.
