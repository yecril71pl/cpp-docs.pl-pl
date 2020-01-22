---
title: Ostrzeżenie kompilatora (poziom 3) C4373
ms.date: 11/04/2016
f1_keywords:
- C4373
helpviewer_keywords:
- C4373
ms.assetid: 670c0ba3-b7d6-4aed-b207-1cb84da3bcde
ms.openlocfilehash: 5891d4679b74695f187fb50bb24fe941882fdcc7
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518351"
---
# <a name="compiler-warning-level-3-c4373"></a>Ostrzeżenie kompilatora (poziom 3) C4373

> "*Function*": funkcja wirtualna przesłania element "*base_function*", poprzednie wersje kompilatora nie przesłonili, gdy parametry różnią się tylko kwalifikatorami const/volatile

## <a name="remarks"></a>Uwagi

Aplikacja zawiera metodę w klasie pochodnej, która zastępuje metodę wirtualną w klasie bazowej, a parametry w metodzie przesłaniania różnią się tylko kwalifikatorem [const](../../cpp/const-cpp.md) lub [volatile](../../cpp/volatile-cpp.md) z parametrów metody wirtualnej. Oznacza to, że kompilator musi powiązać odwołanie do funkcji z metodą w klasie podstawowej lub pochodnej.

Wersje kompilatora przed Visual Studio 2008 wiążą funkcję z metodą w klasie bazowej, a następnie generują komunikat ostrzegawczy. Kolejne wersje kompilatora ignorują kwalifikator `const` lub `volatile`, powiązać funkcję z metodą w klasie pochodnej, a następnie wystawić ostrzeżenie **C4373**. To ostatnie zachowanie jest zgodne ze C++ standardem.

## <a name="example"></a>Przykład

Poniższy przykład kodu generuje ostrzeżenie C4373. Aby rozwiązać ten problem, można wykonać przesłonięcie przy użyciu tych samych kwalifikatorów OKS co podstawowa funkcja członkowska lub jeśli nie zamierzasz utworzyć przesłonięcia, można nadać funkcji w klasie pochodnej inną nazwę.

```cpp
// c4373.cpp
// compile with: /c /W3
#include <stdio.h>
struct Base
{
    virtual void f(int i) {
        printf("base\n");
    }
};

struct Derived : Base
{
    void f(const int i) {  // C4373
        printf("derived\n");
    }
};

int main()
{
    Derived d;
    Base* p = &d;
    p->f(1);
}
```

```Output
derived
```
