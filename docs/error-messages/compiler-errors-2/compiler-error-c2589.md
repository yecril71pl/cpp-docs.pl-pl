---
title: Compiler Error C2589
ms.date: 11/04/2016
f1_keywords:
- C2589
helpviewer_keywords:
- C2589
ms.assetid: 1d7942c7-8a81-4bb4-b272-76a0019e8513
ms.openlocfilehash: 18d8f7130c34f5e1e33bc7aa9b9463f50c243045
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386944"
---
# <a name="compiler-error-c2589"></a>Compiler Error C2589

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