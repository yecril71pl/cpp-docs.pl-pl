---
title: Kompilator ostrzeżenie (poziom 2) C4250 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4250
dev_langs:
- C++
helpviewer_keywords:
- C4250
ms.assetid: d47f7249-6b5a-414b-b2d4-56e5d246a782
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f5797782691385111f0be22854643315f4e596fb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46031442"
---
# <a name="compiler-warning-level-2-c4250"></a>Kompilator ostrzeżenie (poziom 2) C4250

'klasa1': dziedziczy "class2::member" za pośrednictwem pozycji dominującej

Co najmniej dwa elementy członkowskie mają taką samą nazwę. W `class2` jest dziedziczone, ponieważ jest on klasą bazową dla klas, które zawiera ten element członkowski.

Aby pominąć C4250, należy użyć [ostrzeżenie](../../preprocessor/warning.md) pragmy.

Ponieważ wirtualnej klasy bazowej jest współużytkowana przez wiele klas pochodnych, nazwę w klasie pochodnej większą nazwę w klasie bazowej. Na przykład, biorąc pod uwagę następujące hierarchii klas, istnieją dwie definicje func dziedziczone w obrębie romb: wystąpienie vbc::func() za pośrednictwem słabych klasy i dominujący:: func() za pośrednictwem klasy dominującej. Niekwalifikowane wywołanie func() za pośrednictwem obiektu klasy romb zawsze wywołuje wystąpienie dominate:: func().  Gdyby słabe klasy wprowadzenie wystąpienie func() ani definicja będzie dominują i wywołanie zostanie oznaczony jako niejednoznaczny.

```
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

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4250.

```
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

## <a name="example"></a>Przykład

W tym przykładzie pokazano bardziej złożona sytuacja. Poniższy przykład spowoduje wygenerowanie C4250.

```
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