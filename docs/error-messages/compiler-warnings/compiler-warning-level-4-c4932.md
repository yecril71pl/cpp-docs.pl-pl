---
title: Ostrzeżenie kompilatora (poziom 4) C4932
description: Opisuje C4932 ostrzeżeń kompilatora Microsoft C/C++.
ms.date: 08/25/2020
f1_keywords:
- C4932
helpviewer_keywords:
- C4932
ms.assetid: 0b8d88cc-21f6-45cb-a9f5-1795b7db0dfa
ms.openlocfilehash: ece2ae14fd8e1198a97f5e772fcce52c47464878
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898293"
---
# <a name="compiler-warning-level-4-c4932"></a>Ostrzeżenie kompilatora (poziom 4) C4932

> `__identifier(identifier_1)` i `__identifier(identifier_2)` są nieodróżniane

Kompilator nie może rozróżnić parametrów od **`_finally`** i **`__finally`** **`__try`** i **`_try`** jako parametru do [`__identifier`](../../extensions/identifier-cpp-cli.md) . Nie należy próbować używać ich zarówno jako identyfikatorów w tym samym programie, ponieważ spowoduje to błąd [C2374](../../error-messages/compiler-errors-1/compiler-error-c2374.md) .

Poniższy przykład generuje C4932:

```cpp
// C4932.cpp
// compile with: /clr /W4 /WX
int main() {
   int __identifier(_finally) = 245;   // C4932
   int __identifier(__finally) = 25;   // C4932
}
```
