---
title: Błąd kompilatora C2677
ms.date: 11/04/2016
f1_keywords:
- C2677
helpviewer_keywords:
- C2677
ms.assetid: 76bc0b65-f52a-45a6-b6d6-0555f89da9a8
ms.openlocfilehash: 8c318d3c7f78ad2844b7a94a372634886a1ad56d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760351"
---
# <a name="compiler-error-c2677"></a>Błąd kompilatora C2677

Binary "operator": nie odnaleziono operatora globalnego, który ma typ "Type" (lub nie istnieje akceptowalna konwersja)

Aby użyć operatora, należy przeciążyć go dla określonego typu lub zdefiniować konwersję do typu, dla którego zdefiniowano operator.

Poniższy przykład generuje C2677:

```cpp
// C2677.cpp
class C {
public:
   C(){}
} c;

class D {
public:
   D(){}
   operator int(){return 0;}
} d;

int main() {
   int i = 1 >> c;   // C2677
   int j = 1 >> d;   // OK operator int() defined
}
```
