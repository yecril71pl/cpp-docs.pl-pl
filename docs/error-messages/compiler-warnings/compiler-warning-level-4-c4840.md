---
title: Ostrzeżenie kompilatora (poziom 4) C4840
ms.date: 09/13/2018
f1_keywords:
- C4840
helpviewer_keywords:
- C4840
ms.openlocfilehash: 649083d66d0c7a0ef11c742e56cbfb70e2e9b75f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185207"
---
# <a name="compiler-warning-level-4-c4840"></a>Ostrzeżenie kompilatora (poziom 4) C4840

> nieprzenośne użycie klasy "*Type*" jako argumentu funkcji wariadyczne

## <a name="remarks"></a>Uwagi

Klasy lub struktury, które są przenoszone do funkcji wariadyczne, muszą być proste do skopiowania. Podczas przekazywania takich obiektów kompilator po prostu wykonuje kopię bitową i nie wywołuje konstruktora ani destruktora.

To ostrzeżenie jest dostępne począwszy od programu Visual Studio 2017.

## <a name="example"></a>Przykład

Poniższy przykład generuje C4840 i pokazuje, jak to naprawić:

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

W przypadku ciągów skompilowanych i zarządzanych przy użyciu `CStringW`, podane `operator LPCWSTR()` powinny być używane do rzutowania obiektu `CStringW` na wskaźnik ciągu w stylu C oczekiwany przez ciąg formatu:

```cpp
    CStringW str1;
    CStringW str2;
    // ...
    str1.Format("%s", static_cast<LPCWSTR>(str2));
```
