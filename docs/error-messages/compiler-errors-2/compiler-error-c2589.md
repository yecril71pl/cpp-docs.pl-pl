---
title: Błąd kompilatora C2589 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2589
dev_langs:
- C++
helpviewer_keywords:
- C2589
ms.assetid: 1d7942c7-8a81-4bb4-b272-76a0019e8513
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2db5dde898a3e5918eed62b2b32231b5d7ed014f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46046059"
---
# <a name="compiler-error-c2589"></a>Błąd kompilatora C2589

"identyfikator': niedozwolony token po prawej stronie":: "

Jeśli klasy, struktury lub Unii nazwa pojawi się po lewej stronie operatora rozpoznawania zakresu (podwójny dwukropek), token po prawej stronie musi być klasy, struktury lub Unii. W przeciwnym razie wszelkie identyfikator globalny może znajdować się po prawej stronie.

Nie można przeciążać operatora rozpoznawania zakresu.

Poniższy przykład spowoduje wygenerowanie C2589:

```
// C2589.cpp
void Test(){}
class A {};
void operator :: ();   // C2589

int main() {
   ::Test();
}
```