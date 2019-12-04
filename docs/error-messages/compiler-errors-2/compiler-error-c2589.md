---
title: Błąd kompilatora C2589
ms.date: 11/04/2016
f1_keywords:
- C2589
helpviewer_keywords:
- C2589
ms.assetid: 1d7942c7-8a81-4bb4-b272-76a0019e8513
ms.openlocfilehash: 76cc35e57c1577ed23c043740f37c602600da542
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74748505"
---
# <a name="compiler-error-c2589"></a>Błąd kompilatora C2589

"Identyfikator": niedozwolony token po prawej stronie "::"

Jeśli klasa, struktura lub nazwa Unii pojawia się po lewej stronie operatora rozpoznawania zakresu (podwójne dwukropek), token po prawej stronie musi być klasą, strukturą lub składową Unii. W przeciwnym razie każdy identyfikator globalny może pojawić się po prawej stronie.

Nie można obciążać operatora rozpoznawania zakresu.

Poniższy przykład generuje C2589:

```cpp
// C2589.cpp
void Test(){}
class A {};
void operator :: ();   // C2589

int main() {
   ::Test();
}
```
