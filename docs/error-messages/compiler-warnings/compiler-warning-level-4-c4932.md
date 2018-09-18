---
title: Kompilator ostrzeżenie (poziom 4) C4932 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4932
dev_langs:
- C++
helpviewer_keywords:
- C4932
ms.assetid: 0b8d88cc-21f6-45cb-a9f5-1795b7db0dfa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1c9143406fc4b52d50b5dc68215fa796f5100fb7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46053924"
---
# <a name="compiler-warning-level-4-c4932"></a>Kompilator ostrzeżenie (poziom 4) C4932

__identifier(Identifier) i \__identifier(identifier) są nierozróżnialne

Kompilator nie może rozróżnić **_finally** i `__finally` lub `__try` i **_try** jako parametr przekazywany do [__identifier](../../windows/identifier-cpp-cli.md). Możesz nie należy próbować zarówno ich używać jako identyfikatorów w tym samym programie, ponieważ spowoduje ona [C2374](../../error-messages/compiler-errors-1/compiler-error-c2374.md) błędu.

Poniższy przykład spowoduje wygenerowanie C4932:

```
// C4932.cpp
// compile with: /clr /W4 /WX
int main() {
   int __identifier(_finally) = 245;   // C4932
   int __identifier(__finally) = 25;   // C4932
}
```