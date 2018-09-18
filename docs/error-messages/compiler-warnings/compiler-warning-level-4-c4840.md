---
title: Kompilatora (poziom 4) ostrzeżenie C4840 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2018
ms.topic: error-reference
f1_keywords:
- C4840
dev_langs:
- C++
helpviewer_keywords:
- C4840
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c43ce60d319c427877b77a043df7c30bd00edc9b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46025883"
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