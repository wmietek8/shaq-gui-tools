# Paczka testowa po recenzji z 1 listopada 2026

Kod do przeglądu jest podzielony na trzy niezależne PR-y:

1. [#18 — nasłuch wybranego programu](https://github.com/michaldziwisz/shaq-gui-tools/pull/18).
2. [#19 — radio, odsłuch i czytniki ekranu](https://github.com/michaldziwisz/shaq-gui-tools/pull/19).
3. [#20 — klient HTTP, sygnatura i ponowienia](https://github.com/michaldziwisz/shaq-gui-tools/pull/20).

Każdy PR jest oparty na `main` i został sprawdzony osobno. Ta gałąź łączy je
wyłącznie do wspólnej paczki testowej. Rozwiązania nakładających się zmian
znajdują się w commitach łączących gałęzie; nie zastępuje to osobnej oceny PR-ów
ani nie oznacza scalenia przez opiekuna projektu.

W połączonym interfejsie źródła to wyjście, wejście, program i radio.
Katalogi tłumaczeń są łączone, zachowane są osobne zdarzenia radia i
rozpoznawania, a oba rodzaje nasłuchu korzystają z poprawionego klienta HTTP.

Wspólna weryfikacja na Windows / Python 3.11: **278 testów ShaqGUI/ShaqFileGUI**,
w tym rzeczywiste WASAPI, kontrolki wxPython, lokalny serwer radia z FFmpeg
i powiadomienia UI Automation, oraz **105 testów ShaqCast**. Jeden test
rzeczywistego Autostartu jest celowo pomijany. Ostrzeżenia dotyczą istniejącego
wywołania `locale.getdefaultlocale`, nie niepowodzeń testów.

Pełne opisy funkcji i ograniczeń:

- [Nasłuch programu](ZMIANY_PROCES.md)
- [Radio i czytniki](ZMIANY_RADIO_CZYTNIKI.md)
- [Rozpoznawanie](ZMIANY_ROZPOZNAWANIE.md)

Zachowane są nazwy `shaqgui.exe`, `shaqfilegui.exe`, `shaqcast.exe` i bazowa
wersja 0.1.9. Przed podmianą pliku należy zamknąć jego uruchomioną kopię.
Nie dołączono ustawień użytkownika, haseł, historii ani prywatnych nagrań.

Pełny odsłuch JAWS/ZDSR/Narrator oraz całonocna próba radia pozostają
niepotwierdzone; nie są oznaczone jako wykonane.
