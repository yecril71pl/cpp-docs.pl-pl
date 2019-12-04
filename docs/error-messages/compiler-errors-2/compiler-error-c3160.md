---
title: Błąd kompilatora C3160
ms.date: 11/04/2016
f1_keywords:
- C3160
helpviewer_keywords:
- C3160
ms.assetid: a250c433-8adf-43b9-8dee-c3794e09b0a5
ms.openlocfilehash: 4d6f415c8b3c8275ac45ef4d4313021100d9a833
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755151"
---
# <a name="compiler-error-c3160"></a>Błąd kompilatora C3160

"wskaźnik": składowa danych klasy zarządzanej lub WinRT nie może mieć tego typu

Wewnętrzne wskaźniki wyrzucania elementów bezużytecznych mogą wskazywać na wnętrze klasy zarządzanej lub WinRT. Ponieważ są one wolniejsze niż wskaźniki całkowite obiektów i wymagają specjalnej obsługi przez moduł wyrzucania elementów bezużytecznych, nie można zadeklarować wewnętrznych wskaźników zarządzanych jako elementów członkowskich klasy.

Poniższy przykład generuje C3160:

```cpp
// C3160.cpp
// compile with: /clr
ref struct A {
   // cannot create interior pointers inside a class
   interior_ptr<int> pg;   // C3160
   int g;   // OK
   int* pg2;   // OK
};

int main() {
   interior_ptr<int> pg2;   // OK
}
```
