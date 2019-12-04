---
title: Błąd kompilatora C2438
ms.date: 11/04/2016
f1_keywords:
- C2438
helpviewer_keywords:
- C2438
ms.assetid: 3a0ab3ba-d0e4-4d8f-971d-e503397cc827
ms.openlocfilehash: da6443f3f319c864b53f6d077e8bf99faffc5888
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744319"
---
# <a name="compiler-error-c2438"></a>Błąd kompilatora C2438

"Identyfikator": nie można zainicjować danych statycznej klasy za pośrednictwem konstruktora

Konstruktor jest używany do inicjowania statycznej składowej klasy. Statyczne składowe muszą być zainicjowane w definicji poza deklaracją klasy.

Poniższy przykład generuje C2438:

```cpp
// C2438.cpp
struct X {
   X(int i) : j(i) {}   // C2438
   static int j;
};

int X::j;

int main() {
   X::j = 1;
}
```
