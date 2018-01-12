---
title: "C3920 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3920
dev_langs: C++
helpviewer_keywords: C3920
ms.assetid: 66e91f28-ed82-4ce2-bf22-c0c74905b1ed
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b5eeee973258b6d59b7a034e2b71bc453ed7454f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3920"></a>C3920 błąd kompilatora
"operator": nie można definiować operatory przyrostka inkrementacji/dekrementacja WinRT lub wywołanie przyrostkowego operatora CLR WinRT lub CLR operator wywoła odpowiedni prefiks WinRT lub CLR — operator (op_Increment/op_Decrement), ale z przyrostkową semantyką  
  
 Środowisko wykonawcze systemu Windows i CLR nie obsługują operatora przyrostkowego i operatory przyrostek zdefiniowane przez użytkownika nie są dozwolone.  Można zdefiniować operatora prefiksu i będzie można używać operatora prefiksu dla operacji przed i po przyrostu.  
  
 Poniższy przykład generuje C3920 i pokazuje, jak rozwiązywanie problemu:  
  
```  
// C3920.cpp  
// compile with: /clr /LD  
public value struct V {  
   static V operator ++(V me, int)  
   // try the following line instead  
   // static V operator ++(V me)  
   {   // C3920  
      me.m_i++;  
      return me;  
   }  
  
   int m_i;  
};  
  
```