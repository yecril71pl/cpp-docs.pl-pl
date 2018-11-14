---
title: Kompilator ostrzeżenie (poziom 4) C4754
ms.date: 11/04/2016
f1_keywords:
- C4754
helpviewer_keywords:
- C4754
ms.assetid: e0e4606a-754a-4f42-a274-21a34978d21d
ms.openlocfilehash: 82036017188acc3f882e9751096af8ab268fd9db
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2018
ms.locfileid: "51525174"
---
# <a name="compiler-warning-level-4-c4754"></a>Kompilator ostrzeżenie (poziom 4) C4754

Reguły konwersji dla operacji arytmetycznych w porównaniu oznaczają, że jedna gałąź nie może być wykonywane.

Ostrzeżenie C4754 jest wyświetlone, ponieważ wynikiem porównania jest zawsze taki sam. Oznacza to, że jednej gałęzi warunku nigdy nie jest wykonywana, prawdopodobnie ponieważ wyrażenie całkowite skojarzone jest niepoprawny. Ta wada kodu często występuje w niepoprawne tablicy nadmiaru na 64-bitowych architekturach.

Reguły konwersji liczby całkowitej są skomplikowane wiąże się z wielu subtelne pułapek. Jako alternatywę do ustalania każde ostrzeżenie C4754 można zaktualizować kod, aby użyć [Biblioteka SafeInt](../../windows/safeint-library.md).

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

Dodanie `a + b` może spowodować przepełnienie arytmetyczne, zanim wynik zostanie upcast — na wartość 64-bitowych i przypisany do zmiennej 64-bitowych `x`. Oznacza to, że wyboru na `x` byłby nadmiarowy i nigdy nie będzie catch przepełnienie. W tym przypadku kompilator generuje to ostrzeżenie:

```Output
Warning C4754: Conversion rules for arithmetic operations in the comparison at C4754a.cpp (7) mean that one branch cannot be executed. Cast '(a + ...)' to 'ULONG64' (or similar type of 8 bytes).
```

Aby wyeliminować ostrzeżenia, można zmienić w instrukcji przypisania, można rzutować argumentów na 8-bajtowych wartości:

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

`sizeof()` Operator zwraca `size_t`, którego rozmiar jest zależna od architektury. Przykładowy kod działa w 32-bitowych architekturach gdzie `size_t` jest typów 32-bitowych. Jednakże w przypadku 64-bitowych architekturach `size_t` jest typem 64-bitowych. Reguły konwersji dla liczb całkowitych oznaczają, że `a` jest upcast — na wartość 64-bitowych w wyrażeniu `a + b < a` tak, jakby zostałaby napisana `(size_t)a + (size_t)b < (size_t)a`. Gdy `a` i `b` są 32-bitowych liczb całkowitych, operacja dodawania 64-bitowe nigdy nie mogą overflow i nigdy nie przechowuje ograniczenia. W rezultacie kod nigdy nie wykryje warunek przepełnienia liczby całkowitej na 64-bitowych architekturach. W tym przykładzie powoduje, że kompilator będzie to ostrzeżenie:

```Output
Warning C4754: Conversion rules for arithmetic operations in the comparison at C4754b.cpp (7) mean that one branch cannot be executed. Cast '4' to 'ULONG' (or similar type of 4 bytes).
```

Zwróć uwagę, że komunikat ostrzegawczy jawnie wyświetla wartości stałej 4 zamiast oryginalny ciąg źródłowy — przez czas analizy ostrzeżenie napotka naruszającym kod `sizeof(unsigned long)` została przekonwertowana na stałą. W związku z tym masz do śledzenia szczegółów wyrażenie, które w źródle kod jest powiązany z wartości stałej w komunikacie ostrzegawczym. Najbardziej typowe źródła kodu przetłumaczona na stałe w C4754 komunikaty ostrzegawcze są wyrażeniami, takie jak `sizeof(TYPE)` i `strlen(szConstantString)`.

W tym przypadku stałych kodu wyglądać następująco:

```cpp
// Casting the result of sizeof() to unsigned long ensures
// that all the addition operands are 32-bit, so any overflow
// is detected by the check.
if (a + (unsigned long)sizeof(unsigned long) < a)
```

**Uwaga** numer wiersza, określone w ostrzeżenia kompilatora jest ostatni wiersz w instrukcji. W komunikat ostrzegawczy informujący o złożonych instrukcji warunkowej, która jest rozłożona na wiele wierszy wiersza, który zawiera błąd kodu może być kilka wierszy przed wierszem, który jest zgłaszany. Na przykład:

```cpp
unsigned long a;

if (a + sizeof(unsigned long) < a || // incorrect check
    condition1() ||
    a == 0) {    // C4754 warning reported on this line
         // never executes!
         return INVALID_PARAMETER;
}
```