---
title: Błąd kompilatora zasobów RW2002
ms.date: 11/04/2016
f1_keywords:
- RW2002
helpviewer_keywords:
- RW2002
ms.assetid: b1d1a49b-b50b-4b0b-9f09-c7762e2dbe8f
ms.openlocfilehash: 4cd922fff691b524ec9d278ac5948992fc096e09
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396794"
---
# <a name="resource-compiler-error-rw2002"></a>Błąd kompilatora zasobów RW2002

Błąd analizy

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny

1. **Typ akceleratora wymagane (ASCII lub VIRTKEY)**

   `type` Pole **AKCELERATORÓW** instrukcja musi zawierać wartość ASCII lub VIRTKEY.

1. **Rozpocznij w tabeli akceleratora**

   **Rozpocząć** — słowo kluczowe należy natychmiast wykonać **AKCELERATORÓW** — słowo kluczowe.

1. **W oknie dialogowym oczekiwano BEGIN**

   **Rozpocząć** — słowo kluczowe należy natychmiast wykonać **okna DIALOGOWEGO** — słowo kluczowe.

1. **W menu oczekiwano BEGIN**

   **Rozpocząć** — słowo kluczowe należy natychmiast wykonać **MENU** — słowo kluczowe.

1. **W RCData oczekiwano BEGIN**

   **Rozpocząć** — słowo kluczowe należy natychmiast wykonać **RCDATA** — słowo kluczowe.

1. **BEGIN — słowo kluczowe, oczekiwano w tabeli ciągów**

   **Rozpocząć** — słowo kluczowe należy natychmiast wykonać **STRINGTABLE** — słowo kluczowe.

1. **Nie można ponownie używać stałych ciągów**

   W przypadku korzystania z taką samą wartość, dwa razy w **STRINGTABLE** instrukcji. Upewnij się, że są nie mieszanie nakładających się wartości dziesiętnej i szesnastkowej. Każdy identyfikator w **STRINGTABLE** muszą być unikatowe. Osiągnięcie maksymalnej wydajności należy używać stałych ciągłych, uruchamianych w wielu 16.

1. **Kontrolowanie znak poza zakresem [^ A - ^ Z]**

   Znaku kontrolnego w **AKCELERATORÓW** instrukcja jest nieprawidłowa. Znak następujący karetki (**^**) musi należeć do zakresu od A i Z (włącznie).

1. **pusty menu niedozwolone**

   **Zakończenia** — słowo kluczowe jest wyświetlana, zanim wszystkie elementy menu są zdefiniowane w **MENU** instrukcji. Kompilator zasobów nie dopuszcza pustego menu. Upewnij się, że nie masz żadnych otwartych znaki cudzysłowu, w ramach **MENU** instrukcji.

1. **Oczekiwano w oknie dialogowym zakończenia**

   **Zakończenia** — słowo kluczowe musi wystąpić na końcu **okna DIALOGOWEGO** instrukcji. Upewnij się, że nie ma żadnych otwarte oferty pozostanie z poprzednich instrukcji.

1. **END w menu**

   **Zakończenia** — słowo kluczowe musi przypadać na końcu **MENU** instrukcji. Upewnij się, nie masz wszelkie cudzysłowy open lub niezgodne pary **rozpocząć** i **zakończenia** instrukcji.

1. **Oczekiwany przecinek w tabeli akceleratora**

   Kompilator zasobów wymaga przecinka między `event` i *idvalue* pola w **AKCELERATORÓW** instrukcji.

1. **Nazwa klasy kontrolki oczekiwanego**

   `class` Pole **kontroli** instrukcji w **okna DIALOGOWEGO** instrukcja musi być jednym z następujących typów: PRZYCISK, COMBOBOX, Edytuj, pola listy, pasek PRZEWIJANIA, statyczna, lub zdefiniowany przez użytkownika. Upewnij się, że klasa jest poprawna.

1. **Oczekiwano nazwy krój czcionki**

   *Krój czcionki* pole opcji czcionki w **okna DIALOGOWEGO** instrukcja musi być ujęte w podwójny cudzysłów ciąg znaków ASCII. To pole określa nazwę czcionki.

1. **Oczekiwana wartość Identyfikatora dla elementu menuitem**

   **MENU** instrukcja musi zawierać *menuID* pola, który określa nazwę lub liczbę, która identyfikuje zasób menu.

1. **Ciąg oczekiwany menu**

   Każdy **MENUITEM** i **okno PODRĘCZNE** instrukcja musi zawierać *tekstu* pola, które jest ciąg ujęty w znaki podwójnego cudzysłowu, który określa nazwę elementu menu lub okno podręczne menu. A **MENUITEM SEPARATOR** instrukcja wymaga ciągów w cudzysłowach.

1. **Oczekiwana wartość liczbową polecenia**

   Kompilator zasobów oczekiwała liczbową *idvalue* pole **AKCELERATORÓW** instrukcji. Upewnij się, że używasz `#define` stałą, aby określić wartość i że stała jest poprawna.

1. **Oczekiwano stałej liczbowej w tabeli ciągów**

   Stałej liczbowej zdefiniowane w `#define` instrukcji, należy natychmiast wykonać **rozpocząć** — słowo kluczowe w **STRINGTABLE** instrukcji.

1. **Oczekiwano liczbowego w punktach**

   *Pointsize* pole opcji czcionki w **okna DIALOGOWEGO** instrukcja musi być wartością całkowitą z zakresu punktu rozmiar.

1. **Oczekiwano stałej wartości liczbowych okna dialogowego**

   A **okna DIALOGOWEGO** instrukcja wymaga wartości całkowitoliczbowe dla *x, y, szerokość*, i *wysokość* pola. Upewnij się, że te wartości są objęte po **okna DIALOGOWEGO** — słowo kluczowe i że nie są one ujemna.

1. **Oczekiwano ciągu w STRINGTABLE**

   Oczekiwano ciągu po każdym poleceniu *stringid* wartość w **STRINGTABLE** instrukcji.

1. **Oczekiwano ciągu lub stała klawisz skrótu — polecenie**

   Kompilator zasobów nie jest możliwe ustalenie, jakiego rodzaju klucza jest konfigurowana dla akceleratora. `event` Pole **AKCELERATORÓW** instrukcja może być nieprawidłowy.

1. **Oczekiwano liczby dla Identyfikatora**

   Oczekiwano liczby dla `id` pola w instrukcji sterowania **okna DIALOGOWEGO** instrukcji. Upewnij się, że masz wiele lub `#define` poufności informacji dotyczące Identyfikator kontrolki.

1. **Oczekiwano ciągu w cudzysłowie w klasy okien dialogowych**

   `class` Pole opcji klasy w **okna DIALOGOWEGO** instrukcja musi być liczba całkowita lub ciąg ujęty w znaki podwójnego cudzysłowu.

1. **Oczekiwano ciągu w cudzysłowie w tytule okna dialogowego**

   `captiontext` Pole opcji podpis w **okna DIALOGOWEGO** instrukcja musi być ujęte w podwójny cudzysłów ciąg znaków ASCII.

1. **Nie można odnaleźć pliku: Nazwa pliku**

   Nie można odnaleźć pliku określonego w wierszu polecenia kompilator zasobów. Sprawdź, czy plik został przeniesiony do innego katalogu oraz czy nazwy pliku lub ścieżki jest wpisana poprawnie. Pliki są wyszukiwane przy użyciu **INCLUDE** zmiennej środowiskowej lub ustawienie Visual w aplikacji Workbench, jeśli jest dostępny.

1. **Nazwy czcionki musi być porządkowe**

   *Pointsize* pole w instrukcji czcionki musi być liczbą całkowitą, a nie w ciągu.

1. **Nieprawidłowy klawiszy skrótów**

   `event` Pole **AKCELERATORÓW** instrukcji nie zostało rozpoznane lub jest więcej niż dwa znaki.

1. **Typ akceleratora nieprawidłowy (ASCII lub VIRTKEY)**

   `type` Pole **AKCELERATORÓW** instrukcja musi zawierać wartość ASCII lub VIRTKEY.

1. **znak kontrolny nieprawidłowy**

   Znaku kontrolnego w **AKCELERATORÓW** instrukcja jest nieprawidłowa. To prawidłowy znak kontrolny składa się z jednej literze (tylko) po daszek (^).

1. **Nieprawidłowy typ formantu**

   Każdej instrukcji kontroli w **okna DIALOGOWEGO** instrukcja musi mieć jedną z następujących czynności: POLE WYBORU, COMBOBOX, KONTROLKA, CTEXT, DEFPUSHBUTTON, TYPU CZĘŚCI EDITTEXT, GROUPBOX, IKONĘ, LISTBOX, LTEXT, PRZYCISK, RADIOBUTTON, RTEXT, PASEK PRZEWIJANIA. Upewnij się, tych instrukcji sterowania jest poprawna.

1. **Nieprawidłowy typ**

   Typ zasobu nie jest wśród typów zdefiniowanych w pliku WINDOWS.h.

1. **Ciąg tekstowy lub liczbę porządkową, oczekiwano w kontrolce**

   *Tekstu* pole **kontroli** instrukcji w **okna DIALOGOWEGO** instrukcja musi być ciąg tekstowy lub numerem porządkowym referencje dla typu kontrolki. Jeśli przy użyciu numeru porządkowego, upewnij się, że masz `#define` instrukcji dla formantu.

1. **Niedopasowane nawiasy**

   Upewnij się, przypadku zamknięcia co otwartego nawiasu **okna DIALOGOWEGO** instrukcji.

1. **Nieoczekiwana wartość w RCData**

   *Danych pierwotnych* wartości w **RCDATA** instrukcji muszą być liczbami całkowitymi lub ciągów, każda jest oddzielona przecinkiem. Upewnij się, nie Opuść przecinek lub nie Opuść cudzysłów wokół ciągu.

1. **Podtyp nieznany menu**

   *Definicji elementu* pole **MENU** instrukcji może zawierać tylko **MENUITEM** i **okno PODRĘCZNE** instrukcji.