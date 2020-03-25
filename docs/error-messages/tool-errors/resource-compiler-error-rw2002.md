---
title: Błąd kompilatora zasobów RW2002
ms.date: 11/04/2016
f1_keywords:
- RW2002
helpviewer_keywords:
- RW2002
ms.assetid: b1d1a49b-b50b-4b0b-9f09-c7762e2dbe8f
ms.openlocfilehash: 9c5c2824778a679627bd3008276849890f43ac7e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190693"
---
# <a name="resource-compiler-error-rw2002"></a>Błąd kompilatora zasobów RW2002

Błąd analizy

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać ten problem, sprawdzając następujące możliwe przyczyny

1. **Wymagany typ akceleratora (ASCII lub standardowym VIRTKEY)**

   Pole `type` w instrukcji **akceleratorów** musi zawierać wartość ASCII lub standardowym VIRTKEY.

1. **Oczekiwano instrukcji BEGIN w tabeli akceleratora**

   Słowo kluczowe BEGIN musi być **od** razu zgodne ze słowem kluczowym **akceleratorów** .

1. **Oczekiwanie w oknie dialogowym**

   Słowo kluczowe BEGIN musi być **od** razu zgodne ze słowem kluczowym **okna dialogowego** .

1. **Oczekiwanie w menu**

   Słowo kluczowe **BEGIN** musi być bezpośrednio zgodne z słowem kluczowym **menu** .

1. **Oczekiwano rozpoczęcia w RCData**

   Słowo kluczowe **BEGIN** musi być bezpośrednio zgodne ze słowem kluczowym **RCDATA** .

1. **Oczekiwano słowa kluczowego BEGIN w tabeli ciągów**

   Słowo kluczowe BEGIN musi być **od** razu zgodne ze słowem kluczowym " **String** ".

1. **Nie można ponowne użyć stałych ciągu**

   Używasz tej samej wartości dwukrotnie w instrukcji **String** . Upewnij się, że nie Mieszasz nakładających się wartości dziesiętnych i szesnastkowych. Każdy identyfikator w tabeli **ciągów** musi być unikatowy. Aby uzyskać maksymalną wydajność, użyj ciągłych stałych, które zaczynają się od wielokrotności 16.

1. **Znak kontrolny poza zakresem [^ A-^ Z]**

   Znak kontrolny w instrukcji **akceleratorów** jest nieprawidłowy. Znak następujący po karetki ( **^** ) musi należeć do zakresu od a do z, włącznie.

1. **Puste menu są niedozwolone**

   Słowo kluczowe **End** pojawia się przed zdefiniowaniem jakichkolwiek elementów menu w instrukcji **menu** . Kompilator zasobów nie zezwala na używanie pustych menu. Upewnij się, że nie masz żadnych otwartych cudzysłowów w instrukcji **menu** .

1. **Oczekiwano końca w oknie dialogowym**

   Słowo kluczowe **End** musi wystąpić na końcu instrukcji **okna dialogowego** . Upewnij się, że nie ma żadnych otwartych cudzysłowów pozostałych od poprzedniej instrukcji.

1. **Oczekiwano końca w menu**

   Słowo kluczowe **End** musi znajdować się na końcu instrukcji **menu** . Upewnij się, że nie masz żadnych otwartych cudzysłowów lub niepasującej pary instrukcji **BEGIN** i **End** .

1. **Oczekiwano przecinka w tabeli akceleratora**

   Kompilator zasobów wymaga przecinki między `event` i *idvalue* pól w instrukcji **akceleratorów** .

1. **Oczekiwana nazwa klasy kontrolki**

   Pole `class` instrukcji **sterującej** w instrukcji **okna dialogowego** musi być jednym z następujących typów: przycisk, ComboBox, Edytuj, ListBox, SCROLLBAR, static lub zdefiniowany przez użytkownika. Upewnij się, że Klasa jest wpisana poprawnie.

1. **Oczekiwana nazwa kroju czcionki**

   Pole *kroju* czcionki opcji Font w instrukcji **okna dialogowego** musi być ciągiem znaków ASCII ujętym w znaki podwójnego cudzysłowu. To pole określa nazwę czcionki.

1. **Oczekiwana wartość identyfikatora elementu MenuItem**

   Instrukcja **menu** musi zawierać pole *MenuID* , które określa nazwę lub numer identyfikujący zasób menu.

1. **Oczekiwany ciąg menu**

   Każda instrukcja **MenuItem** i **popup** musi zawierać pole *tekstowe* , czyli ciąg ujęty w znaki podwójnego cudzysłowu, który określa nazwę elementu menu lub menu podręcznego. Instrukcja **MenuItem separator** nie wymaga ciągu ujętego w cudzysłów.

1. **Oczekiwana wartość polecenia liczbowego**

   Kompilator zasobów oczekiwał pola numerycznego *idvalue* w instrukcji **akceleratorów** . Upewnij się, że użyto stałej `#define`, aby określić wartość i że stała jest wpisana poprawnie.

1. **Oczekiwano stałej liczbowej w tabeli ciągów**

   Stała numeryczna, zdefiniowana w instrukcji `#define`, musi być od razu zgodna ze słowem kluczowym **BEGIN** w instrukcji **String** .

1. **Oczekiwany rozmiar punktu liczbowego**

   Pole *Pointsize* opcji Font w instrukcji **okna dialogowego** musi być wartością typu Liczba całkowita.

1. **Oczekiwana stała numeryczna okna dialogowego**

   Instrukcja **okna dialogowego** wymaga wartości liczb całkowitych dla pól *x, y, Szerokość*i *wysokość* . Upewnij się, że te wartości są zawarte po słowie kluczowym **okna dialogowego** i że nie są ujemne.

1. **Oczekiwano ciągu w tabeli CIĄGÓW**

   Ciąg jest oczekiwany po każdej wartości *stringid* w instrukcji **String** .

1. **Oczekiwano ciągu lub stałego akceleratora polecenia**

   Kompilator zasobów nie mógł określić, jakiego rodzaju klucz jest skonfigurowany dla akceleratora. Pole `event` w instrukcji **Accelerators** może być nieprawidłowe.

1. **Oczekiwano liczby dla identyfikatora**

   Oczekiwano liczby dla pola `id` instrukcji sterującej w instrukcji **okna dialogowego** . Upewnij się, że dla identyfikatora formantu istnieje instrukcja Number lub `#define`.

1. **Oczekiwano ciągu w cudzysłowie w klasie okna dialogowego**

   Pole `class` opcji CLASS w instrukcji **okna dialogowego** musi być liczbą całkowitą lub ciągiem ujętym w znaki podwójnego cudzysłowu.

1. **Oczekiwano ciągu w cudzysłowie w tytule okna dialogowego**

   Pole `captiontext` opcji CAPTION w instrukcji **okna dialogowego** musi być CIĄGIEM znaków ASCII ujętym w znaki podwójnego cudzysłowu.

1. **Nie znaleziono pliku: filename**

   Nie znaleziono pliku określonego w wierszu polecenia kompilatora zasobów. Sprawdź, czy plik został przeniesiony do innego katalogu i czy nazwa pliku lub ścieżka jest wpisana poprawnie. Pliki są przeszukiwane przy użyciu zmiennej środowiskowej **include** lub ustawienia programu Visual Studio, jeśli jest dostępny.

1. **Nazwy czcionek muszą być liczbami porządkowymi**

   Pole *Pointsize* w instrukcji Font musi być liczbą całkowitą, a nie ciągiem.

1. **Nieprawidłowy akcelerator**

   Pole `event` w instrukcji **akceleratorów** nie zostało rozpoznane lub miało więcej niż dwa znaki.

1. **Nieprawidłowy typ akceleratora (ASCII lub standardowym VIRTKEY)**

   Pole `type` w instrukcji **akceleratorów** musi zawierać wartość ASCII lub standardowym VIRTKEY.

1. **Nieprawidłowy znak kontrolny**

   Znak kontrolny w instrukcji **akceleratorów** jest nieprawidłowy. Prawidłowy znak kontrolny składa się z jednej litery (tylko) po karetki (^).

1. **Nieprawidłowy typ kontrolki**

   Każda instrukcja sterująca w instrukcji **okna dialogowego** musi mieć jedną z następujących wartości: CheckBox, ComboBox, Control, CTEXT, DEFPUSHBUTTON, EditText, pole grupy, ikona, ListBox, LTEXT, przycisk, RadioButton, RTEXT, SCROLLBAR. Upewnij się, że te instrukcje sterujące są poprawnie napisane.

1. **Nieprawidłowy typ**

   Typ zasobu nie należy do typów zdefiniowanych w pliku WINDOWS. h.

1. **W kontrolce oczekiwano ciągu tekstowego lub liczby porządkowej**

   Pole *tekstowe* instrukcji **sterującej** w instrukcji **okna dialogowego** musi być ciągiem tekstowym lub odwołaniem porządkowym do typu formantu. W przypadku używania numeru porządkowego upewnij się, że masz instrukcję `#define` dla kontrolki.

1. **Niedopasowane nawiasy**

   Upewnij się, że wszystkie otwarte nawiasy zostały zamknięte w instrukcji **okna dialogowego** .

1. **Nieoczekiwana wartość w RCData**

   Wartości *danych pierwotnych* w instrukcji **RCDATA** muszą być liczbami całkowitymi lub ciągami, z których każda oddzielona przecinkami. Upewnij się, że nie opuścisz przecinka lub nie opuszczasz znaku cudzysłowu otaczającego ciąg.

1. **Nieznany podtyp menu**

   Pole *definicji elementu* w instrukcji **menu** może zawierać tylko instrukcje **MenuItem** i **popup** .
