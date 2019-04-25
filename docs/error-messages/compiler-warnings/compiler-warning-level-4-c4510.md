---
title: Kompilator ostrzeżenie (poziom 4) C4510
ms.date: 11/04/2016
f1_keywords:
- C4510
helpviewer_keywords:
- C4510
ms.assetid: fd28d1d4-ad27-4dad-94c0-9dba46c93180
ms.openlocfilehash: 80183e9f7ef17cbc37592f36eb8db1df2be94827
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62221093"
---
# <a name="compiler-warning-level-4-c4510"></a>Kompilator ostrzeżenie (poziom 4) C4510

"class": nie można wygenerować konstruktora domyślnego

Kompilator nie może wygenerować Konstruktor domyślny dla określonej klasy, a żaden konstruktor zdefiniowany przez użytkownika została utworzona. Nie można utworzyć obiektów tego typu.

Istnieje kilka sytuacji, w których uniemożliwić kompilatorowi wygenerowanie konstruktora domyślnego, w tym:

- Element członkowski danych const.

- Element członkowski danych, który jest odwołaniem.

Należy utworzyć użytkownika domyślnego konstruktora dla klasy, która inicjuje te składowe.

Poniższy przykład spowoduje wygenerowanie C4510:

```
// C4510.cpp
// compile with: /W4
struct A {
   const int i;
   int &j;
   A& operator=( const A& ); // C4510 expected
   // uncomment the following line to resolve this C4510
   // A(int ii, int &jj) : i(ii), j(jj) {}
};   // C4510

int main() {
}
```