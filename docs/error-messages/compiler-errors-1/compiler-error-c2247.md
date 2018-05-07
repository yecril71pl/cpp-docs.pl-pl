---
title: C2247 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2247
dev_langs:
- C++
helpviewer_keywords:
- C2247
ms.assetid: 72efa03e-615e-4ef9-aede-0a98654b20fd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ed27398ea1f51ccc2ef0d3339446b422c7a503c0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2247"></a>C2247 błąd kompilatora
'Identyfikator' nie jest dostępna, ponieważ "class" używa "specyfikatora" dziedziczy po "class"  
  
 `identifier` jest dziedziczona z klasy, zadeklarowanej jako z dostępem prywatne lub chronione.  
  
 Poniższy przykład generuje C2247:  
  
```  
// C2247.cpp  
class A {  
public:  
   int i;  
};  
class B : private A {};    // B inherits a private A  
class C : public B {} c;   // so even though C's B is public  
int j = c.i;               // C2247, i not accessible  
```  
  
 Ten błąd może być również generowany w wyniku pracy zgodność kompilatora, która została wykonana dla programu Visual Studio .NET 2003: dostęp do kontrolki z chronionych elementów członkowskich. Chroniony element członkowski (n) można uzyskać tylko za pośrednictwem funkcji członkowskiej klasy, która dziedziczy po klasie (A), w której (n) jest elementem członkowskim (B).  
  
 Kod, który jest prawidłowy w Visual Studio .NET 2003 i wersji programu Visual Studio .NET programu Visual C++ należy zadeklarować element członkowski jako przyjaciel typu. Można również zmienić publiczne dziedziczenie.  
  
```  
// C2247b.cpp  
// compile with: /c  
// C2247 expected  
class A {  
public:  
   void f();  
   int n;  
};  
  
class B: protected A {  
   // Uncomment the following line to resolve.  
   // friend void A::f();  
};  
  
void A::f() {  
   B b;  
   b.n;  
}  
```  
  
 C2247 może być również generowany w wyniku pracy zgodność kompilatora, która została wykonana dla programu Visual Studio .NET 2003: base prywatnej klasy teraz niedostępny. Jest klasą podstawową prywatnych z typem klasy (A) nie (B) powinien być dostępny do typu (C), który używa B jako klasę podstawową.  
  
 Kod, który jest prawidłowy w Visual Studio .NET 2003 i wersji programu Visual Studio .NET programu Visual C++ użyj operatora zakresem.  
  
```  
// C2247c.cpp  
// compile with: /c  
struct A {};  
  
struct B: private A {};  
  
struct C : B {  
   void f() {  
      A *p1 = (A*) this;   // C2247  
      // try the following line instead  
      // ::A *p2 = (::A*) this;  
   }  
};  
```