---
title: Kompilatora (poziom 2) ostrzeżenie C4250 | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 4b0a49f42dec57677149ab5c36cfc1ab99822cc4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33291362"
---
# <a name="compiler-warning-level-2-c4250"></a>Kompilator C4250 ostrzegawcze (poziom 2)
"class1": "class2::member" za pośrednictwem dominacja dziedziczy  
  
 Co najmniej dwa elementy członkowskie mają taką samą nazwę. W `class2` jest dziedziczone, ponieważ jest on klasę podstawową dla klas, które zawiera ten element członkowski.  
  
 Aby pominąć C4250, należy użyć [ostrzeżenie](../../preprocessor/warning.md) pragma.  
  
 Ponieważ wirtualna klasa podstawowa jest współużytkowane przez wiele klas pochodnych, nazwę w klasie pochodnej dominuje nazwy w klasie podstawowej. Na przykład, biorąc pod uwagę następujące hierarchii klas, istnieją dwie definicje func dziedziczone w obrębie romb: wystąpienie vbc::func() za pośrednictwem klasy słabe i dominujące:: func() za pośrednictwem klasy dominującej. Niekwalifikowane wywołania func() za pośrednictwem obiektu klasy romb zawsze wywołuje wystąpienie dominate:: func().  Jeżeli słabe klasy wprowadzać wystąpieniem func(), ani definicji czy dominują w aplikacjach i wywołanie zostanie oznaczony jako niejednoznaczne.  
  
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
 Poniższy przykład generuje C4250.  
  
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
 W tym przykładzie pokazano sytuację bardziej złożonych. Poniższy przykład generuje C4250.  
  
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