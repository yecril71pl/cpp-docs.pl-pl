---
title: Błąd kompilatora C2775
ms.date: 11/04/2016
f1_keywords:
- C2775
helpviewer_keywords:
- C2775
ms.assetid: 9c488508-ade0-48f1-b94f-d538d15f807a
ms.openlocfilehash: be858c7508aa520f78ec144b02738af02099b49b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74740055"
---
# <a name="compiler-error-c2775"></a>Błąd kompilatora C2775

"Identyfikator": brak metody "Get" skojarzonej z tą właściwością

Element członkowski danych zadeklarowany za pomocą atrybutu rozszerzonego [Właściwości](../../cpp/property-cpp.md) nie ma określonej funkcji `get`, ale wyrażenie próbuje pobrać jego wartość.

Poniższy przykład generuje C2775:

```cpp
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
