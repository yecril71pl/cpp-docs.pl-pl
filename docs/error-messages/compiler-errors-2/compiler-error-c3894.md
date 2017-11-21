---
title: "C3894 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3894
dev_langs: C++
helpviewer_keywords: C3894
ms.assetid: 6d5ac903-1dea-431d-8e3a-cebca4342983
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 46dffabb57e871e1635738434e7efb4812850379
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3894"></a>C3894 błąd kompilatora
"var": wykorzystanie wartości l elementu członkowskiego danych initonly jest dozwolone tylko w konstruktorze wystąpienia klasy "class"  
  
 Statyczne [initonly](../../dotnet/initonly-cpp-cli.md) elementy członkowskie danych można użyć tylko jako l wartości ich w punkcie deklaracji lub w konstruktorze statycznym.  
  
 Elementy członkowskie danych initonly (niestatyczna) wystąpienia można użyć tylko jako l wartości ich w punkcie deklaracji lub w konstruktorach wystąpień (niestatyczna).  
  
 Poniższy przykład generuje C3894:  
  
```  
// C3894.cpp  
// compile with: /clr  
ref struct Y1 {  
   initonly static int data_var = 0;  
  
public:  
   // class constructor  
   static Y1() {  
      data_var = 99;   // OK  
      System::Console::WriteLine("in static constructor");  
   }  
  
   // not the class constructor  
   Y1(int i) {  
      data_var = i;   // C3894  
   }  
  
   static void Test() {}  
  
};  
  
int main() {  
   Y1::data_var = 88;   // C3894  
   int i = Y1::data_var;  
   Y1 ^ MyY1 = gcnew Y1(99);  
   Y1::Test();  
}  
```