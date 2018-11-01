---
title: Błąd kompilatora C2775
ms.date: 11/04/2016
f1_keywords:
- C2775
helpviewer_keywords:
- C2775
ms.assetid: 9c488508-ade0-48f1-b94f-d538d15f807a
ms.openlocfilehash: b0f04a64354f549115c8636cf6130d6e96470016
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50547163"
---
# <a name="compiler-error-c2775"></a>Błąd kompilatora C2775

'Identyfikator': Brak metody "get" jest skojarzony z tą właściwością

Element członkowski danych zadeklarowana za pomocą [właściwość](../../cpp/property-cpp.md) nie ma atrybutów rozszerzonych `get` określonych funkcji, ale próbuje pobrać wartość wyrażenia.

Poniższy przykład spowoduje wygenerowanie C2775:

```
// C2775.cpp
struct A {
   __declspec(property(put=PutProp2, get=GetProp2)) int prop2;
   int GetProp2(){return 0;}
   void PutProp2(int){}

   __declspec(property(put=PutProp)) int prop;
   int PutProp(void){}

};

int main() {
   A* pa = new A;
   int x;
   x = pa->prop;   // C2775
   x = pa->prop2;
}
```