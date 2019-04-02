---
title: Kompilator ostrzeżenie (poziom 4) C4932
ms.date: 11/04/2016
f1_keywords:
- C4932
helpviewer_keywords:
- C4932
ms.assetid: 0b8d88cc-21f6-45cb-a9f5-1795b7db0dfa
ms.openlocfilehash: cd37ee67545918991b286d16d0fe27b47414b3c3
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58769826"
---
# <a name="compiler-warning-level-4-c4932"></a>Kompilator ostrzeżenie (poziom 4) C4932

__identifier(Identifier) i \__identifier(identifier) są nierozróżnialne

Kompilator nie może rozróżnić **_finally** i `__finally` lub `__try` i **_try** jako parametr przekazywany do [__identifier](../../extensions/identifier-cpp-cli.md). Możesz nie należy próbować zarówno ich używać jako identyfikatorów w tym samym programie, ponieważ spowoduje ona [C2374](../../error-messages/compiler-errors-1/compiler-error-c2374.md) błędu.

Poniższy przykład spowoduje wygenerowanie C4932:

```
// C4932.cpp
// compile with: /clr /W4 /WX
int main() {
   int __identifier(_finally) = 245;   // C4932
   int __identifier(__finally) = 25;   // C4932
}
```