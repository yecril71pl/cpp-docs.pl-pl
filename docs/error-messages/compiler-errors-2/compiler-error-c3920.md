---
title: C3920 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3920
dev_langs:
- C++
helpviewer_keywords:
- C3920
ms.assetid: 66e91f28-ed82-4ce2-bf22-c0c74905b1ed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6ced0a0f8fa2b6694de4dd901d71f6721e12493b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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