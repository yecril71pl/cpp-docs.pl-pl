---
title: Kompilator ostrzeżenie (poziom 1) C4305
ms.date: 1/17/2018
f1_keywords:
- C4305
helpviewer_keywords:
- C4305
ms.openlocfilehash: 3f9116b0e7bdd9ee13c42b48f44da4b090f41ccd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50649127"
---
# <a name="compiler-warning-level-1-c4305"></a>Kompilator ostrzeżenie (poziom 1) C4305

> "*kontekstu*': obcinanie z '*type1*"to"*type2*"

## <a name="remarks"></a>Uwagi

To ostrzeżenie zostanie wyświetlone, gdy wartość jest konwertowana na mniejszy typ podczas inicjowania lub jako argument konstruktora, co spowoduje utratę informacji.

## <a name="example"></a>Przykład

Ten przykład przedstawia dwa sposoby, które można napotkać tego ostrzeżenia:

```cpp
// C4305.cpp
// Compile by using: cl /EHsc /W4 C4305.cpp

struct item
{
    item(float) {}
};

int main()
{
    float f = 2.71828;          // C4305 'initializing'
    item i(3.14159);            // C4305 'argument'
    return static_cast<int>(f);
}
```

Aby rozwiązać ten problem, inicjowanie przy użyciu poprawnego typu wartości lub użyć jawnego rzutowania do poprawnego typu. Na przykład użyć **float** literału, takich jak 2.71828f zamiast **double** (domyślny typ zmiennoprzecinkowych literałów) do zainicjowania **float** zmiennej, lub do przekazania do Konstruktor pobierający **float** argumentu.
