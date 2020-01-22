---
title: Ostrzeżenie kompilatora (poziom 4) C4703
ms.date: 11/04/2016
f1_keywords:
- C4703
helpviewer_keywords:
- C4703
ms.assetid: 5dad454e-69e3-4931-9168-050a861c05f8
ms.openlocfilehash: 5033490550f318cab65f984cab81b08102641c9d
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518364"
---
# <a name="compiler-warning-level-4-c4703"></a>Ostrzeżenie kompilatora (poziom 4) C4703

Użyto potencjalnie niezainicjowanej zmiennej wskaźnika lokalnego "name"

*Nazwa* zmiennej wskaźnika lokalnego mogła zostać użyta bez przypisywania wartości. Może to prowadzić do nieprzewidzianych wyników.

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

[Ostrzeżenie kompilatora (poziom 4) C4701](../../error-messages/compiler-warnings/compiler-warning-level-4-c4701.md)<br/>
[Ostrzeżenia,/SDL i ulepszanie wykrywania zmiennej niezainicjowanej](https://www.microsoft.com/security/blog/2012/06/06/warnings-sdl-and-improving-uninitialized-variable-detection/)
