---
title: Kompilator ostrzeżenie (poziom 1) C4602 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4602
dev_langs:
- C++
helpviewer_keywords:
- C4602
ms.assetid: c1f0300f-e2a2-4c9e-a7c3-4c7318d10509
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3cae5810f94ed9c3feb22de145c7e12e1a7d813b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46033319"
---
# <a name="compiler-warning-level-1-c4602"></a>Kompilator ostrzeżenie (poziom 1) C4602

\#pragma pop_macro: "name — makro" nie poprzedniej dyrektywy #pragma push_macro dla tego identyfikatora

Jeśli używasz [pop_macro](../../preprocessor/pop-macro.md) dla konkretnego makra, należy najpierw przekazana nazwa tego makra, które [push_macro](../../preprocessor/push-macro.md). Na przykład poniższy przykład spowoduje wygenerowanie C4602:

```
// C4602.cpp
// compile with: /W1
int main()
{
   #pragma pop_macro("x")   // C4602 x is not on the stack
}
```