---
title: Kompilator ostrzeżenie (poziom 4) C4510 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4510
dev_langs:
- C++
helpviewer_keywords:
- C4510
ms.assetid: fd28d1d4-ad27-4dad-94c0-9dba46c93180
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f2aaf7286c2e900629a18d7df5824ef4b7af1f5f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46048971"
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