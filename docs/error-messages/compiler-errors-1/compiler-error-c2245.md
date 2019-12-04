---
title: Błąd kompilatora C2245
ms.date: 11/04/2016
f1_keywords:
- C2245
helpviewer_keywords:
- C2245
ms.assetid: 08aaeadf-10ec-485a-b2a6-6e775289082b
ms.openlocfilehash: bc3f8e17d8d3746bdc243193f1349939bca5e164
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759207"
---
# <a name="compiler-error-c2245"></a>Błąd kompilatora C2245

nieistniejąca funkcja członkowska określona jako Friend (Sygnatura funkcji składowej nie pasuje do żadnego przeciążenia)

Kompilator nie znalazł funkcji określonej jako zaprzyjaźnionej.

Poniższy przykład generuje C2245:

```cpp
// C2245.cpp
// compile with: /c
class B {
   void f(int i);
};

class A {
   int m_i;
   friend void B::f(char);   // C2245
   // try the following line instead
   // friend void B::f(int);
};

void B::f(int i) {
   A a;
   a.m_i = 0;
}
```
