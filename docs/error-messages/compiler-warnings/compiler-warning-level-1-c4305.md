---
title: Ostrzeżenie kompilatora (poziom 1) C4305
ms.date: 01/17/2018
f1_keywords:
- C4305
helpviewer_keywords:
- C4305
ms.openlocfilehash: 567442bc48487e4f7d1f905f871d15f913646e87
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233291"
---
# <a name="compiler-warning-level-1-c4305"></a>Ostrzeżenie kompilatora (poziom 1) C4305

> "*Context*": obcinanie z "*Type1*" do "*Type2*"

## <a name="remarks"></a>Uwagi

To ostrzeżenie jest generowane, gdy wartość zostanie przekonwertowana na mniejszy typ w inicjacji lub jako argument konstruktora, co spowodowało utratę informacji.

## <a name="example"></a>Przykład

Ten przykład pokazuje dwa sposoby wyświetlania tego ostrzeżenia:

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

Aby rozwiązać ten problem, należy zainicjować przy użyciu wartości poprawnego typu lub użyć jawnego rzutowania do poprawnego typu. Na przykład użyj **`float`** literału, takiego jak 2.71828 f zamiast **`double`** (domyślny typ dla literałów zmiennoprzecinkowych), aby zainicjować **`float`** zmienną lub przekazać do konstruktora, który przyjmuje **`float`** argument.
