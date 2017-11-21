---
title: "Kompilatora (poziom 1) ostrzeżenie C4358 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4358
dev_langs: C++
helpviewer_keywords: C4358
ms.assetid: a9848f84-14b3-405e-81bf-ee3e91a51511
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8f09125123ea075c1d0c9fbce5fdd432dfa64407
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4358"></a>Kompilator C4358 ostrzegawcze (poziom 1)
"operator": zwracany typ połączonych delegatów nie jest "void"; zwrócona wartość jest niezdefiniowana  
  
 Dwa obiekty delegowane zostały połączone i wartości zwracanej nie jest void. Jeśli są łączone dwa delegatów o wartości zwracanych z systemem innym niż void, kompilator nie będzie można wykonać przypisania prawidłowego, jeśli używana jest zwracana wartość delegata.  
  
 Poniższy przykład generuje C4358:  
  
```  
// C4358.cpp  
// compile with: /clr /W1  
delegate int D();  
delegate void E();  
  
ref class X {  
   int i;  
public:  
   X(int ii) : i(ii) {}  
   int f() {  
      return i;  
   }  
};  
  
ref class Y {  
   int i;  
public:  
   Y() {}  
   void g() {}  
};  
  
int main() {  
   D^ d = gcnew D(gcnew X(1), &X::f);  
   D^ d2 = gcnew D(gcnew X(2), &X::f);  
  
   d += d2;   // C4358  
   int j = d();   // return value indeterminate  
  
   E^ e = gcnew E(gcnew Y, &Y::g);  
   E^ e2 = gcnew E(gcnew Y, &Y::g);  
   e += e2;   // OK  
}  
```