---
title: Ostrzeżenie kompilatora (poziom 4) C4932
ms.date: 11/04/2016
f1_keywords:
- C4932
helpviewer_keywords:
- C4932
ms.assetid: 0b8d88cc-21f6-45cb-a9f5-1795b7db0dfa
ms.openlocfilehash: 992e047f31e4a30edd29ba6110bf119d2bc8928b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230600"
---
# <a name="compiler-warning-level-4-c4932"></a>Ostrzeżenie kompilatora (poziom 4) C4932

__identifier (identyfikator) i \_ _identifier (identyfikator) są nierozróżniane

Kompilator nie może rozróżnić między **_finally** i **`__finally`** lub `__try` **_try** jako parametr przesłany do [__identifier](../../extensions/identifier-cpp-cli.md). Nie należy próbować używać ich zarówno jako identyfikatorów w tym samym programie, ponieważ spowoduje to błąd [C2374](../../error-messages/compiler-errors-1/compiler-error-c2374.md) .

Poniższy przykład generuje C4932:

```cpp
// C4932.cpp
// compile with: /clr /W4 /WX
int main() {
   int __identifier(_finally) = 245;   // C4932
   int __identifier(__finally) = 25;   // C4932
}
```
