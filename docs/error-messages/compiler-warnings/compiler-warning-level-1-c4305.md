---
title: Kompilator ostrzeżenie (poziom 1) C4305 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 1/17/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4305
dev_langs:
- C++
helpviewer_keywords:
- C4305
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 88ae0fb38b7e6af14525906e90486a68ce22ee56
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46086827"
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
