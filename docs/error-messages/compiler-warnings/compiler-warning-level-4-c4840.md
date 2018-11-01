---
title: Kompilatora (poziom 4) ostrzeżenie C4840
ms.date: 09/13/2018
f1_keywords:
- C4840
helpviewer_keywords:
- C4840
ms.openlocfilehash: a757004659c1a9d2ce858cfae5ddfbc6c024d782
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50586436"
---
# <a name="compiler-warning-level-4-c4840"></a>Kompilatora (poziom 4) ostrzeżenie C4840

> nieprzenośne użycie klasy*typu*"jako argumentu do funkcji ze zmienną liczbą argumentów

## <a name="remarks"></a>Uwagi

Klasy lub struktury, które są przekazywane do funkcji ze zmienną liczbą argumentów musi być kopiowania. Podczas przekazywania takie obiekty, kompilator po prostu sprawia, że kopia bitowa i nie wywołuje konstruktor lub destruktor.

To ostrzeżenie jest dostępne począwszy od wersji programu Visual Studio 2017.

## <a name="example"></a>Przykład

Poniższy przykład generuje C4840 i pokazuje, jak go naprawić:

```cpp
// C4840.cpp
// compile by using: cl /EHsc /W4 C4840.cpp
#include <stdio.h>

int main()
{
    struct S {
        S(int i) : i(i) {}
        S(const S& other) : i(other.i) {}
        operator int() { return i; }
    private:
        int i;
    } s(0);

    printf("%i\n", s); // warning C4840 : non-portable use of class 'main::S'
                       // as an argument to a variadic function
    // To correct the error, you can perform a static cast
    // to convert the object before passing it:
    printf("%i\n", static_cast<int>(s));
}
```

Ciągi utworzone i zarządzane przy użyciu `CStringW`, podane `operator LPCWSTR()` powinien być używany do rzutowania `CStringW` obiektu wskaźnik ciąg stylu C, oczekiwany przez ciąg formatu:

```cpp
    CStringW str1;
    CStringW str2;
    // ...
    str1.Format("%s", static_cast<LPCWSTR>(str2));
```