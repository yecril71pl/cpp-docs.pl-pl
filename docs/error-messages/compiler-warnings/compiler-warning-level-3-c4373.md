---
title: Kompilatora (poziom 3) ostrzeżenie C4373 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4373
dev_langs:
- C++
helpviewer_keywords:
- C4373
ms.assetid: 670c0ba3-b7d6-4aed-b207-1cb84da3bcde
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fda965fe80fc26731cde7be5a71540e6454a7360
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-3-c4373"></a>Kompilator C4373 ostrzegawcze (poziom 3)

> "*funkcja*": przesłonięcia funkcji wirtualnych*base_function*", poprzednie wersje kompilatora nie przesłaniały, gdy parametry różniły się tylko przez kwalifikatory const/volatile

## <a name="remarks"></a>Uwagi

Aplikacja zawiera metody w klasie pochodnej zastępujący wirtualnej metody w klasie podstawowej i parametrów w metodę zastępującą różnią się jedynie [const](../../cpp/const-cpp.md) lub [volatile](../../cpp/volatile-cpp.md) kwalifikator z Parametry metody wirtualnej. Oznacza to, kompilator musi powiązać funkcji odwołania do metody w jednej bazie lub klasy.

Wersje kompilatora przed Visual Studio 2008 powiązać funkcji do metody w klasie podstawowej, a następnie wystawiania komunikat ostrzegawczy. Ignoruj kolejne wersje kompilatora `const` lub `volatile` kwalifikator, powiązania funkcji do metody w klasie pochodnej, a następnie wystawiania ostrzeżenie **C4373**. To zachowanie ostatnie spełnia C++ standard.

## <a name="example"></a>Przykład

Poniższy przykład kodu generuje ostrzeżenie C4373. Aby rozwiązać ten problem, możesz ustalić zastąpienie, użyj tego samego kwalifikatorów CV jako funkcję podstawowego elementu członkowskiego, lub jeśli nieprzeznaczonych do tworzenia zastąpienia, należy przyznać funkcji w klasie pochodnej inną nazwę.

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

void main()
{
    Derived d;
    Base* p = &d;
    p->f(1);
}
```

```Output
derived
```