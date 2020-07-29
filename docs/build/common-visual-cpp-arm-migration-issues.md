---
title: Typowe problemy przy migracji Visual C++ ARM
ms.date: 05/06/2019
ms.assetid: 0f4c434e-0679-4331-ba0a-cc15dd435a46
ms.openlocfilehash: 889eed2b02362f33446cd9441ef84f406817b01a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224074"
---
# <a name="common-visual-c-arm-migration-issues"></a>Typowe problemy przy migracji Visual C++ ARM

W przypadku korzystania z kompilatora języka Microsoft C++ (MSVC) ten sam kod źródłowy C++ może generować różne wyniki na architekturze ARM niż w przypadku architektury x86 i x64.

## <a name="sources-of-migration-issues"></a>Źródła problemów migracji

Wiele problemów, które mogą wystąpić podczas migrowania kodu z architektury x86 lub x64 do architektury ARM, jest związanych z konstrukcjami kodu źródłowego, które mogą wywoływać niezdefiniowane, zdefiniowane w implementacji lub nieokreślone zachowanie.

*Niezdefiniowane zachowanie* jest zachowaniem, że standard C++ nie definiuje, i jest to spowodowane operacją, która nie ma uzasadnionego wyniku: na przykład, konwertowanie wartości zmiennoprzecinkowej na liczbę całkowitą bez znaku lub przesunięcie wartości przez wiele pozycji, które są ujemne lub przekracza liczbę bitów w podwyższonym typie.

*Zachowanie zdefiniowane w implementacji* jest zachowaniem, że standard C++ wymaga, aby dostawca kompilatora został zdefiniowany i dokument. Program może bezpiecznie polegać na zachowaniu zdefiniowanym przez implementację, nawet jeśli nie może być przenośny. Przykłady zachowania zdefiniowanego w implementacji obejmują rozmiary wbudowanych typów danych i ich wymagania dotyczące wyrównania. Przykład operacji, która może mieć wpływ na zachowanie zdefiniowane przez implementację, uzyskuje dostęp do listy argumentów zmiennych.

*Nieokreślone zachowanie* jest zachowaniem, że standard C++ pozostawia celowo Niedeterministyczny. Chociaż zachowanie jest uznawane za niedeterministyczne, konkretne wywołania nieokreślonych zachowań są określane przez implementację kompilatora. Nie jest jednak wymagane, aby dostawca kompilatora wstępnie określił wynik lub zagwarantować spójność zachowań między porównywalnymi wywołaniami, i nie ma wymagań dotyczących dokumentacji. Przykładem nieokreślonego zachowania jest kolejność, w której są oceniane wyrażenia podrzędne, które zawierają argumenty do wywołania funkcji.

Inne problemy z migracją mogą być przypisane do różnic sprzętowych między architekturami ARM i x86 lub x64, które różnią się w zależności od języka C++. Na przykład model silnej pamięci architektury x86 i x64 udostępnia **`volatile`** kwalifikowane zmienne pewnych dodatkowych właściwości, które zostały użyte do ułatwienia niektórych rodzajów komunikacji między wątkami w przeszłości. Chociaż słaby model pamięci architektury ARM nie obsługuje tego zastosowania, ani nie jest to wymagane przez standard C++.

> [!IMPORTANT]
> Chociaż **`volatile`** pozyskuje pewne właściwości, których można użyć do wdrożenia ograniczonej formy komunikacji między wątkami w architekturze x86 i x64, te dodatkowe właściwości nie są wystarczające do zaimplementowania komunikacji między wątkami. Standard C++ zaleca zaimplementowanie takiej komunikacji przy użyciu odpowiednich elementów pierwotnych synchronizacji.

Ponieważ różne platformy mogą w inny sposób wyrazić takie zachowanie, portowanie oprogramowania między platformami może być trudne i podatne na błędy, jeśli zależy to od zachowania określonej platformy. Chociaż wiele z tych rodzajów zachowań może być przestrzegane i mogą być stabilne, polega na nich, że jest to co najmniej nieprzenośne, a w przypadku niezdefiniowanego lub nieokreślonego zachowania jest również błędem. Nawet zachowanie, które jest cytowane w tym dokumencie, nie powinno być używane i może ulec zmianie w przyszłych kompilatorach lub implementacjach procesora CPU.

## <a name="example-migration-issues"></a>Przykładowe problemy z migracją

W pozostałej części niniejszego dokumentu opisano, jak różne zachowanie tych elementów języka C++ może dawać różne wyniki na różnych platformach.

### <a name="conversion-of-floating-point-to-unsigned-integer"></a>Konwersja zmiennoprzecinkowej na liczbę całkowitą bez znaku

W architekturze ARM konwersja wartości zmiennoprzecinkowej na 32-bitową liczbę całkowitą zwiększy się do najbliższej wartości, która może reprezentować, jeśli wartość zmiennoprzecinkowa znajduje się poza zakresem, który może reprezentować liczbę całkowitą. W przypadku architektur x86 i x64 konwersja jest zawijana wokół, jeśli liczba całkowita jest niepodpisana lub jest ustawiona na-2147483648, jeśli liczba całkowita jest podpisana. Żadna z tych architektur nie obsługuje bezpośrednio konwersji wartości zmiennoprzecinkowych na mniejsze typy całkowite. Zamiast tego konwersje są wykonywane do 32 bitów, a wyniki są obcinane do mniejszego rozmiaru.

W przypadku architektury ARM kombinacja nasycenia i obcinania oznacza, że konwersja na typy bez znaku prawidłowo zwiększa nasycenie mniejszych typów bez znaku, gdy zwiększa nasycenie 32-bitową liczbę całkowitą, ale generuje obcięty wynik dla wartości, które są większe niż mniejszy typ może reprezentować, ale za mały, aby zmniejszyć liczbę całkowitą 32-bitową. Konwersja jest również skracana odpowiednio do 32-bitowych liczb całkowitych ze znakiem, ale obcinanie liczb całkowitych ze znakiem jest równe-1 dla dodatniie nasycone wartości i 0 w przypadku wartości ujemnie nasycone. Konwersja na mniejszą liczbę całkowitą ze znakiem powoduje, że nieprzewidywalne wyniki.

W przypadku architektur x86 i x64, kombinacji zachowań zawijania dla nieoznaczonych konwersji liczb całkowitych i jawnej wartości wyceny dla zapisywanych konwersji liczb całkowitych w przepełnieniu, a także obcinanie wyników, które są zbyt duże, jeśli są zbyt długie.

Te platformy różnią się również sposobem obsługi konwersji NaN (not-Number) na typy całkowite. W usłudze ARM funkcja NaN jest konwertowana na 0x00000000; w systemach x86 i x64 jest konwertowany na 0x80000000.

Przekształcenie zmiennoprzecinkowe może być używane tylko wtedy, gdy wiadomo, że wartość znajduje się w zakresie typu całkowitego, który jest konwertowany na.

### <a name="shift-operator---behavior"></a>Zachowanie operatora przesunięcia ( \<\< >>)

W architekturze ARM wartość może zostać przesunięta w lewo lub w prawo do 255 bitów, zanim wzorzec zacznie powtarzać. W architekturze x86 i x64 wzorzec jest powtarzany w każdej wielokrotności 32, chyba że źródło wzorca jest zmienną 64-bitową; w takim przypadku wzorzec powtarza się w każdej wielokrotności 64 w x64, a każda wielokrotność 256 w x86, w której jest stosowana implementacja oprogramowania. Na przykład dla zmiennej 32-bitowej, która ma wartość 1 przesuniętą w lewo o pozycję 32, na platformie ARM wynikiem jest 0, w przypadku procesora x86 wynik wynosi 1, a w przypadku architektury x64 wynik jest również 1. Jeśli jednak źródło wartości jest zmienną 64-bitową, wynikiem wszystkich trzech platform jest 4294967296, a wartość nie jest "Zawijaj", dopóki nie zostanie przesunięta pozycja 64 pozycji na architekturze x64 lub 256 w pozycji ARM i x86.

Ponieważ wynik operacji przesunięcia, która przekracza liczbę bitów w typie źródła, jest niezdefiniowany, kompilator nie musi mieć spójnego zachowania we wszystkich sytuacjach. Na przykład jeśli oba operandy przesunięcia są znane w czasie kompilacji, kompilator może zoptymalizować program przy użyciu wewnętrznej procedury do wstępnego obliczenia wyniku przesunięcia, a następnie podstawiając wynik zamiast operacji przesunięcia. Jeśli wartość przesunięcia jest zbyt duża lub ujemna, wynik procedury wewnętrznej może być inny niż wynik tego samego wyrażenia przesunięcia, co wykonywane przez procesor CPU.

### <a name="variable-arguments-varargs-behavior"></a>Zmienne argumenty (VarArgs)

W architekturze ARM parametry z listy argumentów zmiennych, które są przekazane na stosie, podlegają wyrównaniu. Na przykład parametr 64-bitowy jest wyrównany na granicy 64-bitowej. Na procesorach x86 i x64 argumenty, które są przekazane na stosie, nie podlegają wyrównaniu i ściśle pakowaniu. Różnica ta może spowodować, że funkcja wariadyczne będzie `printf` odczytywać adresy pamięci, które zostały zamierzone jako uzupełnienie na platformie ARM, jeśli oczekiwany układ listy zmiennych argumentów nie jest dokładnie dopasowany, mimo że może ona działać w przypadku podzestawu niektórych wartości w architekturze x86 lub x64. Rozważmy następujący przykład:

```C
// notice that a 64-bit integer is passed to the function, but '%d' is used to read it.
// on x86 and x64 this may work for small values because %d will "parse" the low-32 bits of the argument.
// on ARM the calling convention will align the 64-bit value and the code will print a random value
printf("%d\n", 1LL);
```

W takim przypadku usterkę można naprawić, upewniając się, że jest używana poprawna specyfikacja formatu, aby wyrównać wyrównanie argumentu. Ten kod jest poprawny:

```C
// CORRECT: use %I64d for 64-bit integers
printf("%I64d\n", 1LL);
```

### <a name="argument-evaluation-order"></a>Kolejność szacowania argumentów

Ponieważ procesory ARM, x86 i x64 są tak różne, mogą one przedstawić różne wymagania dla implementacji kompilatora, a także różne możliwości optymalizacji. Z tego względu, wraz z innymi czynnikami, takimi jak ustawienia konwencji wywoływania i optymalizacji, kompilator może oszacować argumenty funkcji w innej kolejności w różnych architekturach lub w przypadku zmiany innych czynników. Może to spowodować nieoczekiwane zmiany zachowania aplikacji, która opiera się na określonej kolejności oceny.

Ten rodzaj błędu może wystąpić, gdy argumenty funkcji mają wpływ na inne argumenty funkcji w tym samym wywołaniu. Zazwyczaj ten rodzaj zależności jest łatwy do uniknięcia, ale może być czasami słonięty przez zależności, które są trudne do rozpoznać lub przez przeciążanie operatora. Rozważmy następujący przykład kodu:

```cpp
handle memory_handle;

memory_handle->acquire(*p);
```

Jest to dobrze zdefiniowane, ale jeśli `->` i `*` są przeciążone operatory, ten kod jest tłumaczony na coś podobnego do poniższego:

```cpp
Handle::acquire(operator->(memory_handle), operator*(p));
```

A jeśli istnieje zależność między `operator->(memory_handle)` i `operator*(p)` , kod może polegać na określonej kolejności oceny, nawet jeśli oryginalny kod wygląda na to, że nie ma możliwej zależności.

### <a name="volatile-keyword-default-behavior"></a>zachowanie domyślne nietrwałego słowa kluczowego

Kompilator MSVC obsługuje dwie różne interpretacje **`volatile`** kwalifikatora magazynu, które można określić za pomocą przełączników kompilatora. [/Volatile: MS](reference/volatile-volatile-keyword-interpretation.md) Switch wybiera rozszerzoną semantykę nietrwałą firmy Microsoft, która gwarantuje silne porządkowanie, tak jak w przypadku tradycyjnego przypadku x86 i x64 ze względu na model silnej pamięci w tych architekturach. Przełącznik [/volatile: ISO](reference/volatile-volatile-keyword-interpretation.md) wybiera ścisłą niestandardową semantykę języka C++, która nie gwarantuje silnej kolejności.

W architekturze ARM wartość domyślna to **/volatile: ISO** , ponieważ procesory ARM mają słabo uporządkowany model pamięci i ponieważ oprogramowanie ARM nie ma starszej wersji opartej na rozszerzonej semantyce **/volatile: MS** i zazwyczaj nie ma interfejsu z oprogramowaniem, które wykonuje. Jednak nadal jest to wygodne lub nawet wymagane do skompilowania programu ARM, aby można było korzystać z semantyki rozszerzonej. Na przykład może być zbyt kosztowne, aby port programu mógł używać semantyki ISO C++, lub oprogramowanie sterownika może być zgodne z tradycyjną semantyką do poprawnego działania. W takich przypadkach można użyć przełącznika **/volatile: MS** ; Aby jednak utworzyć ponownie tradycyjną semantykę nietrwałą dla elementów docelowych ARM, kompilator musi wstawiać bariery pamięci wokół każdego odczytu lub zapisu **`volatile`** zmiennej w celu wymuszenia silnej kolejności, co może mieć negatywny wpływ na wydajność.

W architekturze x86 i x64 wartością domyślną jest **/volatile: MS** , ponieważ większość oprogramowania, które zostało już utworzone dla tych architektur przy użyciu MSVC opiera się na nich. Podczas kompilowania programów x86 i x64 można określić przełącznik **/volatile: ISO** , aby uniknąć niepotrzebnych zależności tradycyjnych nietrwałych semantyki i podwyższyć poziom przenoszenia.

## <a name="see-also"></a>Zobacz także

[Konfigurowanie Visual C++ dla procesorów ARM](configuring-programs-for-arm-processors-visual-cpp.md)
