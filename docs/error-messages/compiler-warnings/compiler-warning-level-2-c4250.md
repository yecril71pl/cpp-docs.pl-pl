---
title: Ostrzeżenie kompilatora (poziom 2) C4250
ms.date: 11/04/2016
f1_keywords:
- C4250
helpviewer_keywords:
- C4250
ms.assetid: d47f7249-6b5a-414b-b2d4-56e5d246a782
ms.openlocfilehash: 10064784e1124ac365475f00b3577d22f5e7f3f1
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686525"
---
# <a name="compiler-warning-level-2-c4250"></a>Ostrzeżenie kompilatora (poziom 2) C4250

"Class1": dziedziczy element "'klasa:: member" za pośrednictwem pozycji dominującej

Co najmniej dwa składowe mają tę samą nazwę. Ta wartość `class2` jest dziedziczona, ponieważ jest klasą bazową dla innych klas, które zawierały ten element członkowski.

Aby pominąć C4250, użyj dyrektywy pragma [ostrzeżenia](../../preprocessor/warning.md) .

Ponieważ wirtualna Klasa bazowa jest współdzielona przez wiele klas pochodnych, nazwa w klasie pochodnej dominuje nazwę w klasie bazowej. Na przykład, uwzględniając następującą hierarchię klas, istnieją dwie definicje funkcji Func dziedziczone w obrębie rombu: wystąpienie VBC:: Func () za pomocą klasy słabej oraz elementu dominującego:: Func () za pomocą klasy dominującej. Niekwalifikowane wywołanie funkcji Func () za pomocą obiektu klasy Diamond, zawsze wywołuje wystąpienie dominuje:: Func ().  Jeśli słaba Klasa miała wprowadzić wystąpienie funkcji Func (), żadna definicja nie zostanie użyta, a wywołanie zostanie oflagowane jako niejednoznaczne.

## <a name="examples"></a>Przykłady

```cpp
// C4250.cpp
// compile with: /c /W2
#include <stdio.h>
struct vbc {
   virtual void func() { printf("vbc::func\n"); }
};

struct weak : public virtual vbc {};

struct dominant : public virtual vbc {
   void func() { printf("dominant::func\n"); }
};

struct diamond : public weak, public dominant {};

int main() {
   diamond d;
   d.func();   // C4250
}
```

Poniższy przykład generuje C4250.

```cpp
// C4250_b.cpp
// compile with: /W2 /EHsc
#include <iostream>
using namespace std;
class A {
public:
   virtual operator int () {
      return 2;
   }
};

class B : virtual public A {
public:
   virtual operator int () {
      return 3;
   }
};

class C : virtual public A {};

class E : public B, public C {};   // C4250

int main() {
   E eObject;
   cout << eObject.operator int() << endl;
}
```

Ten przykład pokazuje bardziej skomplikowaną sytuację. Poniższy przykład generuje C4250.

```cpp
// C4250_c.cpp
// compile with: /W2 /EHsc
#include <iostream>
using namespace std;

class V {
public:
   virtual int f() {
      return 1024;
   }
};

class B : virtual public V {
public:
   int b() {
      return f(); // B::b() calls V::f()
   }
};

class M : virtual public V {
public:
   int f() {
      return 7;
   }
};

// because of dominance, f() is M::f() inside D,
// changing the meaning of B::b's f() call inside a D
class D : public B, public M {};   // C4250

int main() {
   D d;
   cout << "value is: " << d.b();   // invokes M::f()
}
```
