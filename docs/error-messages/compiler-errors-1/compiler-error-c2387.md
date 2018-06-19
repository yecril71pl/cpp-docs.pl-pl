---
title: C2387 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2387
dev_langs:
- C++
helpviewer_keywords:
- C2387
ms.assetid: 6847b8e1-ffac-458d-ab88-0c92f72f2527
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e490e2c0016649054c557026a5fa691162c40c07
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33225600"
---
# <a name="compiler-error-c2387"></a>C2387 błąd kompilatora
"type": niejednoznaczna klasa podstawowa  
  
 Kompilator nie można jednoznacznie rozpoznać wywołania funkcji, ponieważ funkcja istnieje w więcej niż jedną klasę podstawową.  
  
 Aby rozwiązać ten problem, usuń jedną z klas podstawowych z dziedziczenia lub jawnie zakwalifikować wywołania funkcji.  
  
 Poniższy przykład generuje C2387:  
  
```  
// C2387.cpp  
namespace N1 {  
   struct B {  
      virtual void f() {  
      }  
   };  
}  
  
namespace N2 {  
   struct B {  
      virtual void f() {  
      }  
   };  
}  
  
struct D : N1::B, N2::B {  
   virtual void f() {  
      B::f();   // C2387  
      // try the following line instead  
      // N1::B::f();  
   }  
};  
  
int main() {  
   D aD;  
   aD.f();  
}  
```