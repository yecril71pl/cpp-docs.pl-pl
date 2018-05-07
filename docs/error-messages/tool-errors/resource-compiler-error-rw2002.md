---
title: Błąd kompilatora zasobów RW2002 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RW2002
dev_langs:
- C++
helpviewer_keywords:
- RW2002
ms.assetid: b1d1a49b-b50b-4b0b-9f09-c7762e2dbe8f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bb42298a7140439e3578281de60075f540b09175
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="resource-compiler-error-rw2002"></a>Błąd kompilatora zasobów RW2002
Błąd analizy  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny  
  
1.  **Wymagany typ akceleratora (ASCII lub VIRTKEY)**  
  
     `type` w **AKCELERATORÓW** instrukcja musi zawierać wartość ASCII lub VIRTKEY.  
  
2.  **Rozpocznij w tabeli akceleratora**  
  
     **Rozpocząć** — słowo kluczowe musi występować zaraz po **AKCELERATORÓW** — słowo kluczowe.  
  
3.  **W oknie dialogowym POCZĄTKOWY**  
  
     **Rozpocząć** — słowo kluczowe musi występować zaraz po **okna DIALOGOWEGO** — słowo kluczowe.  
  
4.  **Rozpocznij w menu**  
  
     **Rozpocząć** — słowo kluczowe musi występować zaraz po **MENU** — słowo kluczowe.  
  
5.  **Oczekiwano w RCData POCZĄTKOWY**  
  
     **Rozpocząć** — słowo kluczowe musi występować zaraz po **RCDATA** — słowo kluczowe.  
  
6.  **BEGIN — słowo kluczowe, oczekiwano w tabeli ciągów**  
  
     **Rozpocząć** — słowo kluczowe musi występować zaraz po **STRINGTABLE** — słowo kluczowe.  
  
7.  **Nie można ponownie użyć stałe typu string**  
  
     Używane są dwa razy w tej samej wartości **STRINGTABLE** instrukcji. Upewnij się, że są nie mieszanie nakładających się wartości dziesiętnej i szesnastkowej. Każdy identyfikator w **STRINGTABLE** muszą być unikatowe. Użyj stałych ciągłe, uruchamianych na wielokrotnością 16 z maksymalną wydajnością.  
  
8.  **Kontrolowanie znak poza zakresem [^ A - ^ Z]**  
  
     Znak kontrolny w **AKCELERATORÓW** instrukcja jest nieprawidłowa. Znak następujący karetkę (**^**) musi należeć do zakresu od A i Z wartościami granicznymi.  
  
9. **pusty menu niedozwolone**  
  
     **Zakończenia** — słowo kluczowe pojawia się, aby wszystkie elementy menu są zdefiniowane w **MENU** instrukcji. Kompilator zasobów nie zezwala na puste menu. Upewnij się, że nie masz żadnych Otwórz znaki cudzysłowu w ciągu **MENU** instrukcji.  
  
10. **W oknie dialogowym oczekiwany końcowy**  
  
     **Zakończenia** — słowo kluczowe muszą występować na końcu **okna DIALOGOWEGO** instrukcji. Upewnij się, że nie ma żadnych otwarte oferty w lewo z powyższych instrukcji.  
  
11. **END w menu**  
  
     **Zakończenia** — słowo kluczowe musi występować na końcu **MENU** instrukcji. Upewnij się, że nie masz wszelkie cudzysłowy open lub niedopasowane pary **rozpocząć** i **zakończenia** instrukcje.  
  
12. **Oczekiwano przecinka w tabeli akceleratora**  
  
     Kompilator zasobów wymaga przecinka między `event` i *idvalue* pól w **AKCELERATORÓW** instrukcji.  
  
13. **Nazwa klasy oczekiwanego formantu**  
  
     `class` Pole **kontroli** instrukcji w **okna DIALOGOWEGO** instrukcja musi być jedną z następujących typów: przycisk, COMBOBOX, Edycja, LISTBOX, pasek PRZEWIJANIA, STATYCZNEJ, lub zdefiniowanej przez użytkownika. Upewnij się, że klasa jest poprawna.  
  
14. **Oczekiwano nazwy krój czcionki**  
  
     *Krój* pole opcji czcionki w **okna DIALOGOWEGO** instrukcja musi być ujęta w znaki podwójnego cudzysłowu ciąg znaków ASCII. To pole określa nazwę czcionki.  
  
15. **Oczekiwana wartość Identyfikatora dla elementu menuitem**  
  
     **MENU** musi zawierać instrukcji *menuID* pola, które określa nazwę lub numer identyfikujący zasób menu.  
  
16. **Ciąg oczekiwany menu**  
  
     Każdy **MENUITEM** i **PODRĘCZNEGO** musi zawierać instrukcji *tekst* pola, które jest ujęta w znaki podwójnego cudzysłowu ciąg określający nazwę elementu menu lub menu podręczne menu. A **SEPARATORA MENUITEM** instrukcja wymaga ciągu w cudzysłowie.  
  
17. **Oczekiwano wartości liczbowych poleceń**  
  
     Kompilator zasobów oczekiwała liczbową *idvalue* w **AKCELERATORÓW** instrukcji. Upewnij się, że użyto `#define` stała w celu określenia wartości i że stała jest poprawna.  
  
18. **Oczekiwano stałej liczbowej w tabeli ciągów**  
  
     Stałej liczbowej zdefiniowane w `#define` instrukcji, musi występować zaraz po **rozpocząć** — słowo kluczowe w **STRINGTABLE** instrukcji.  
  
19. **Oczekiwano liczbowe w punktach**  
  
     *Pointsize* pole opcji czcionki w **okna DIALOGOWEGO** instrukcja musi być punkt rozmiar całkowitą.  
  
20. **Oczekiwano stałej liczbowej okna dialogowego**  
  
     A **okna DIALOGOWEGO** instrukcja wymaga wartości całkowite dla *x, y, szerokość*, i *wysokość* pola. Upewnij się, że te wartości są objęte po **okna DIALOGOWEGO** — słowo kluczowe i że nie są one ujemna.  
  
21. **Oczekiwano ciągu w STRINGTABLE**  
  
     Oczekiwano ciągu po każdym poleceniu *identyfikator ciągu* wartość w **STRINGTABLE** instrukcji.  
  
22. **Oczekiwano ciągu lub stała klawisz skrótu — polecenie**  
  
     Kompilator zasobów nie mógł ustalić, jakiego rodzaju klucza jest konfigurowana dla akceleratora. `event` w **AKCELERATORÓW** instrukcja może być nieprawidłowy.  
  
23. **oczekiwany numer dla Identyfikatora**  
  
     Oczekiwany numer dla `id` pole w instrukcji sterowania **okna DIALOGOWEGO** instrukcji. Upewnij się, że masz liczbą lub `#define` instrukcji dla identyfikatora formantu.  
  
24. **Oczekiwano ciągu w cudzysłowie w okna dialogowego — klasa**  
  
     `class` Pole opcji klasy w **okna DIALOGOWEGO** instrukcja musi być liczbą całkowitą lub ciąg ujęty w podwójny cudzysłów.  
  
25. **Oczekiwano ciągu w cudzysłowie w tytule okna dialogowego**  
  
     `captiontext` Pole opcji podpisu w **okna DIALOGOWEGO** instrukcja musi być ujęta w znaki podwójnego cudzysłowu ciąg znaków ASCII.  
  
26. **Nie znaleziono pliku: Nazwa pliku**  
  
     Nie można odnaleźć pliku określonego w wierszu polecenia kompilatora zasobów. Sprawdź, czy plik został przeniesiony do innego katalogu i określa, czy nazwa pliku lub ścieżka jest wpisana poprawnie. Pliki są wyszukiwane przy użyciu **INCLUDE** zmiennej środowiskowej lub ustawienie Visual Workbench, jeśli jest dostępna.  
  
27. **Nazwy czcionki musi być porządkowe**  
  
     *Pointsize* pola w instrukcji czcionki musi być liczbą całkowitą, a nie ciągu.  
  
28. **Nieprawidłowy klawiszy skrótów**  
  
     `event` w **AKCELERATORÓW** instrukcji nie został rozpoznany lub więcej niż dwóch znaków długości.  
  
29. **Typ akceleratora nieprawidłowe (ASCII lub VIRTKEY)**  
  
     `type` w **AKCELERATORÓW** instrukcja musi zawierać wartość ASCII lub VIRTKEY.  
  
30. **Nieprawidłowy formant znaków**  
  
     Znak kontrolny w **AKCELERATORÓW** instrukcja jest nieprawidłowa. Znak kontrolny prawidłowy składa się z jednej literze (tylko) po daszek (^).  
  
31. **Nieprawidłowy typ formantu**  
  
     Każda instrukcja kontroli w **okna DIALOGOWEGO** instrukcja musi być jedną z następujących: pole wyboru, COMBOBOX, kontroli, CTEXT, DEFPUSHBUTTON, typu części EDITTEXT, GROUPBOX, IKONA, LISTBOX, LTEXT, przycisku polecenia, RADIOBUTTON, RTEXT, pasek PRZEWIJANIA. Upewnij się, te instrukcje sterowania są poprawne.  
  
32. **Nieprawidłowy typ**  
  
     Typ zasobu nie między typów zdefiniowanych w pliku WINDOWS.h.  
  
33. **Ciąg tekstowy lub numer oczekiwano w formancie**  
  
     *Tekst* pole **kontroli** instrukcji w **okna DIALOGOWEGO** instrukcja musi być ciąg tekstowy lub odwołanie {numer porządkowy dla typu formantu. Jeśli przy użyciu numeru porządkowego, upewnij się, że masz `#define` instrukcji dla formantu.  
  
34. **Niedopasowane nawiasy**  
  
     Upewnij się, że każdy nawiasu otwierającego zostały zamknięte **okna DIALOGOWEGO** instrukcji.  
  
35. **Nieoczekiwana wartość w RCData**  
  
     *Danych pierwotnych* wartości w **RCDATA** instrukcji muszą być liczbami całkowitymi lub ciągów, oddzielonych przecinkami. Upewnij się, nie Opuść przecinek ani Opuść znak cudzysłowu wokół ciąg.  
  
36. **Podtyp nieznany menu**  
  
     *Definicji elementu* pole **MENU** instrukcja może zawierać tylko **MENUITEM** i **PODRĘCZNEGO** instrukcje.