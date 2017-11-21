---
title: "C2171 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2171
dev_langs: C++
helpviewer_keywords: C2171
ms.assetid: a80343b5-ab3f-4413-b6f1-3ce9d7e519e5
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 08b5b7c00ed54b14597995d8923a5c36c7b87289
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2171"></a>C2171 błąd kompilatora
"operator": niedozwolone na operandach typu "type"  
  
 Operator jednoargumentowy jest używany z typem nieprawidłowy argument.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C2171.  
  
```  
// C2171.cpp  
int main() {  
   double d, d1;  
   d = ~d1;   // C2171  
  
   // OK  
   int d2 = 0, d3 = 0;  
   d2 = ~d3;  
}  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C2171.  
  
```  
// C2171_b.cpp  
// compile with: /c  
class A {  
public:  
   A() { STF( &A::D ); }  
  
   void D() {}  
   void DTF() {  
      (*TF)();   // C2171  
      (this->*TF)();   // OK  
   }  
  
   void STF(void (A::*fnc)()) {  
      TF = fnc;  
   }  
  
private:  
   void (A::*TF)();  
};  
```