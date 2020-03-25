---
title: Ostrzeżenie kompilatora (poziom 4) C4754
ms.date: 11/04/2016
f1_keywords:
- C4754
helpviewer_keywords:
- C4754
ms.assetid: e0e4606a-754a-4f42-a274-21a34978d21d
ms.openlocfilehash: f55d40044fef58275ad0e1fbd281b5f1af43c243
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198136"
---
# <a name="compiler-warning-level-4-c4754"></a>Ostrzeżenie kompilatora (poziom 4) C4754

Reguły konwersji dla operacji arytmetycznych w porównaniu oznaczają, że jedna gałąź nie może być wykonana.

Zostanie wygenerowane Ostrzeżenie C4754, ponieważ wynik porównania jest zawsze taki sam. Oznacza to, że jedna z gałęzi warunku nigdy nie jest wykonywana, prawdopodobnie ze względu na to, że skojarzone wyrażenie całkowite jest niepoprawne. Ten defekt kodu często występuje w nieprawidłowej liczbie przepełnień całkowitych w przypadku architektury 64-bitowych.

Reguły konwersji liczb całkowitych są złożone i istnieje wiele delikatnych pułapek. Jako alternatywę do naprawienia każdego ostrzeżenia C4754 można zaktualizować kod, aby użyć [biblioteki SafeInt](../../safeint/safeint-library.md).

## <a name="example"></a>Przykład

Ten przykład generuje C4754:

```cpp
// C4754a.cpp
// Compile with: /W4 /c
#include "errno.h"

int sum_overflow(unsigned long a, unsigned long b)
{
   unsigned long long x = a + b; // C4754

   if (x > 0xFFFFFFFF)
   {
      // never executes!
      return EOVERFLOW;
   }
   return 0;
}
```

Dodanie `a + b` może spowodować przepełnienie arytmetyczne, zanim wynik zostanie przerzutowany do wartości 64-bitowej i przypisany do zmiennej 64-bitowej `x`. Oznacza to, że sprawdzanie `x` jest nadmiarowe i nigdy nie będzie przechwytywać przepełnienia. W takim przypadku kompilator emituje to ostrzeżenie:

```Output
Warning C4754: Conversion rules for arithmetic operations in the comparison at C4754a.cpp (7) mean that one branch cannot be executed. Cast '(a + ...)' to 'ULONG64' (or similar type of 8 bytes).
```

Aby wyeliminować ostrzeżenie, można zmienić instrukcję przypisania, aby rzutować operandy na wartości 8-bajtowe:

```cpp
// Casting one operand is sufficient to force all the operands in
// the addition be upcast according to C/C++ conversion rules, but
// casting both is clearer.
unsigned long long x =
   (unsigned long long)a + (unsigned long long)b;
```

## <a name="example"></a>Przykład

Następny przykład generuje również C4754.

```cpp
// C4754b.cpp
// Compile with: /W4 /c
#include "errno.h"

int wrap_overflow(unsigned long a)
{
   if (a + sizeof(unsigned long) < a) // C4754
   {
      // never executes!
      return EOVERFLOW;
   }
   return 0;
}
```

Operator `sizeof()` zwraca `size_t`, którego rozmiar jest zależny od architektury. Przykładowy kod działa na 32-bitowych architekturach, w których `size_t` jest typem 32-bitowym. Jednak w przypadku architektur 64-bitowych `size_t` jest typem 64-bitowym. Reguły konwersji dla liczb całkowitych oznaczają, że `a` jest rzutowana na wartość 64-bitową w wyrażeniu `a + b < a` tak, jakby była zapisywana `(size_t)a + (size_t)b < (size_t)a`. Gdy `a` i `b` są 32-bitowymi liczbami całkowitymi, operacja dodawania 64-bitowego nigdy nie może przekroczyć przeciążenia, a ograniczenie nigdy nie utrzymuje. W związku z tym kod nigdy nie wykrywa w architekturze 64-bitowych warunek przepełnienia liczby całkowitej. Ten przykład powoduje, że kompilator emituje to ostrzeżenie:

```Output
Warning C4754: Conversion rules for arithmetic operations in the comparison at C4754b.cpp (7) mean that one branch cannot be executed. Cast '4' to 'ULONG' (or similar type of 4 bytes).
```

Należy zauważyć, że komunikat ostrzegawczy jawnie wyświetla wartość stałą 4 zamiast oryginalnego ciągu źródłowego — przez czas, gdy analiza ostrzeżeń napotka nieprawidłowy kod, `sizeof(unsigned long)` został już przekonwertowany na stałą. W związku z tym może być konieczne śledzenie, które wyrażenie w kodzie źródłowym jest skojarzone z wartością stałą w komunikacie ostrzegawczym. Najpopularniejsze źródła kodu rozpoznane jako stałe w komunikatach ostrzeżeń C4754 są wyrażeniami, takimi jak `sizeof(TYPE)` i `strlen(szConstantString)`.

W takim przypadku stały kod będzie wyglądać następująco:

```cpp
// Casting the result of sizeof() to unsigned long ensures
// that all the addition operands are 32-bit, so any overflow
// is detected by the check.
if (a + (unsigned long)sizeof(unsigned long) < a)
```

**Uwaga** Numer wiersza, do którego odwołuje się ostrzeżenie kompilatora, jest ostatnim wierszem instrukcji. W komunikacie ostrzegawczym dotyczącym złożonej instrukcji warunkowej, która jest rozłożona na wiele wierszy, wiersz, który ma defekt kodu, może być kilka wierszy przed wierszem, który jest raportowany. Na przykład:

```cpp
unsigned long a;

if (a + sizeof(unsigned long) < a || // incorrect check
    condition1() ||
    a == 0) {    // C4754 warning reported on this line
         // never executes!
         return INVALID_PARAMETER;
}
```
