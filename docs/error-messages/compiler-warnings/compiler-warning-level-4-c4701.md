---
title: Ostrzeżenie kompilatora (poziom 4) C4701
ms.date: 11/04/2016
f1_keywords:
- C4701
helpviewer_keywords:
- C4701
ms.assetid: d7c76c66-1f3f-4d3c-abe4-5d94c84a5a1f
ms.openlocfilehash: b83ad810da06de1f9d640477f73d4393c932054a
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518390"
---
# <a name="compiler-warning-level-4-c4701"></a>Ostrzeżenie kompilatora (poziom 4) C4701

Użyto potencjalnie niezainicjowanej zmiennej lokalnej "name"

*Nazwa* zmiennej lokalnej mogła zostać użyta bez przypisywania wartości. Może to prowadzić do nieprzewidzianych wyników.

## <a name="example"></a>Przykład

Poniższy kod generuje C4701 i C4703.

```cpp
#include <malloc.h>

void func(int size)
{
    void* p;
    if (size < 256) {
        p = malloc(size);
    }

    if (p != nullptr) // C4701 and C4703
        free(p);
}

int main()
{
    func(9);
}
```

```Output
c:\src\test.cpp(10) : warning C4701: potentially uninitialized local variable 'p' used
c:\src\test.cpp(10) : warning C4703: potentially uninitialized local pointer variable 'p' used
```

Aby poprawić to ostrzeżenie, zainicjuj zmienną, jak pokazano w tym przykładzie:

```cpp
#include <malloc.h>

void func(int size)
{
    void* p = nullptr;
    if (size < 256) {
        p = malloc(size);
    }

    if (p != nullptr)
        free(p);
}

int main()
{
    func(9);
}
```

## <a name="see-also"></a>Zobacz także

[Ostrzeżenie kompilatora (poziom 4) C4703](../../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md)<br/>
[Ostrzeżenia,/SDL i ulepszanie wykrywania zmiennej niezainicjowanej](https://www.microsoft.com/security/blog/2012/06/06/warnings-sdl-and-improving-uninitialized-variable-detection/)
