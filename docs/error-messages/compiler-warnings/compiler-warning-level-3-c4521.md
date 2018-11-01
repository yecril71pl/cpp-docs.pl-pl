---
title: Kompilator ostrzeżenie (poziom 3) C4521
ms.date: 11/04/2016
f1_keywords:
- C4521
helpviewer_keywords:
- C4521
ms.assetid: 057d770c-ebcf-44cd-b943-1b1bb1ceaa8c
ms.openlocfilehash: 887526810f7e65280adcde422ef871a67ccdde1f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50591818"
---
# <a name="compiler-warning-level-3-c4521"></a>Kompilator ostrzeżenie (poziom 3) C4521

"class": określono wiele konstruktorów kopiujących

Klasa ma wiele konstruktorów kopiujących jednego typu. Ostrzeżenie to jest informacyjna; Konstruktory są wywoływane w programach.

Użyj [ostrzeżenie](../../preprocessor/warning.md) pragma, aby pominąć to ostrzeżenie.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4521.

```
// C4521.cpp
// compile with: /EHsc /W3
#include <iostream>

using namespace std;
class A {
public:
   A() { cout << "A's default constructor" << endl; }
   A( A &o ) { cout << "A&" << endl; }
   A( const A &co ) { cout << "const A&" << endl; }   // C4521
};

int main() {
   A o1;         // Calls default constructor.
   A o2( o1 );   // Calls A( A& ).
   const A o3;   // Calls default constructor.
   A o4( o3 );   // Calls A( const A& ).
}
```