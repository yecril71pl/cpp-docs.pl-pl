---
title: Kompilator ostrzeżenie (poziom 2) C4356
ms.date: 11/04/2016
f1_keywords:
- C4356
helpviewer_keywords:
- C4356
ms.assetid: 3af3defe-de33-43b6-bd6c-2c2e09e34f3f
ms.openlocfilehash: 218aac1cc98d9b119490a547d63b4b5ee83e53df
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50447362"
---
# <a name="compiler-warning-level-2-c4356"></a>Kompilator ostrzeżenie (poziom 2) C4356

'składowa': nie można zainicjować statycznej składowej danych za pośrednictwem pochodnej klasy

Inicjowanie statyczna składowa danych został niewłaściwie sformatowany. Kompilator akceptowane inicjowania. Aby uniknąć ostrzeżenia, należy zainicjować elementu członkowskiego za pośrednictwem klasy bazowej.

Użyj [ostrzeżenie](../../preprocessor/warning.md) pragma, aby pominąć to ostrzeżenie.

Poniższy przykład spowoduje wygenerowanie C4356:

```
// C4356.cpp
// compile with: /W2 /EHsc
#include <iostream>

template <class T>
class C {
   static int n;
};

class D : C<int> {};

int D::n = 0; // C4356
// try the following line instead
// int C<int>::n = 0;

class A {
public:
   static int n;
};

class B : public A {};

int B::n = 10;   // C4356
// try the following line instead
// int A::n = 99;

int main() {
   using namespace std;
   cout << B::n << endl;
}
```