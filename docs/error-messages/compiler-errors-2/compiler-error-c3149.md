---
title: "C3149 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3149
dev_langs: C++
helpviewer_keywords: C3149
ms.assetid: cf6e2616-2f06-46da-8a8a-d449cb481c51
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: dc5abf02a3210ca3d7bd858662e0c02d4f42d75d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3149"></a>C3149 błąd kompilatora
'type': nie można użyć tego typu, w tym miejscu bez najwyższego poziomu "char"  
  
 Deklaracja nie został poprawnie określony.  
  
 Na przykład można mieć zdefiniowany typu CLR w zakresie globalnym i próbował utworzyć zmienną typu jako część definicji. Ponieważ zmienne globalne typów CLR nie są dozwolone, kompilator wygeneruje C3149.  
  
 Aby rozwiązać ten problem, należy zadeklarować zmienne typy CLR wewnątrz definicji funkcji lub typu.  
  
 Poniższy przykład generuje C3149:  
  
```  
// C3149.cpp  
// compile with: /clr  
using namespace System;  
int main() {  
   // declare an array of value types   
   array< Int32 ^> IntArray;   // C3149  
   array< Int32>^ IntArray2;   // OK  
}  
```  
  
 Poniższy przykład generuje C3149:  
  
```  
// C3149b.cpp  
// compile with: /clr /c  
delegate int MyDelegate(const int, int);  
void Test1(MyDelegate m) {}   // C3149  
void Test2(MyDelegate ^ m) {}   // OK  
```  
