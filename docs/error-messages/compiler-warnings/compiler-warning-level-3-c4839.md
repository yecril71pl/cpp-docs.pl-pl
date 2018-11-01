---
title: Kompilator ostrzeżenie (poziom 3) C4839
ms.date: 09/13/2018
f1_keywords:
- C4839
helpviewer_keywords:
- C4839
ms.assetid: f4f99066-9258-4330-81a8-f4a75a1d95ee
ms.openlocfilehash: 09b6e5b8dc984b35df7de96f5cf8610f2b0f16af
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536645"
---
# <a name="compiler-warning-level-3-c4839"></a>Kompilator ostrzeżenie (poziom 3) C4839

> niestandardowe użycie klasy*typu*"jako argumentu do funkcji ze zmienną liczbą argumentów

Klasy lub struktury, które są przekazywane do funkcji ze zmienną liczbą argumentów, takich jak `printf` musi być kopiowania. Podczas przekazywania takie obiekty, kompilator po prostu sprawia, że kopia bitowa i nie wywołuje konstruktor lub destruktor.

To ostrzeżenie jest dostępne począwszy od wersji programu Visual Studio 2017.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4839:

```cpp
// C4839.cpp
// compile by using: cl /EHsc /W3 C4839.cpp
#include <atomic>
#include <memory>
#include <stdio.h>

int main()
{
    std::atomic<int> i(0);
    printf("%i\n", i); // error C4839: non-standard use of class 'std::atomic<int>'
                        // as an argument to a variadic function
                        // note: the constructor and destructor will not be called;
                        // a bitwise copy of the class will be passed as the argument
                        // error C2280: 'std::atomic<int>::atomic(const std::atomic<int> &)':
                        // attempting to reference a deleted function
}
```

Aby poprawić ten błąd, należy wywołać funkcji składowej, która zwraca typ trywialne,

```cpp
    std::atomic<int> i(0);
    printf("%i\n", i.load());
```

Ciągi utworzone i zarządzane przy użyciu `CStringW`, podane `operator LPCWSTR()` powinien być używany do rzutowania `CStringW` obiektu do wskaźnika C, oczekiwany przez ciąg formatu.

```cpp
    CStringW str1;
    CStringW str2;
    // ...
    str1.Format("%s", static_cast<LPCWSTR>(str2));
```