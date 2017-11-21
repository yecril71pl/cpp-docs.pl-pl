---
title: "C2033 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2033
dev_langs: C++
helpviewer_keywords: C2033
ms.assetid: fd5a1637-9db2-4c98-a7cc-b63b39737cd9
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ba0fcc5d0938c796c94e6201be18d6c1fb6158b0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2033"></a>C2033 błąd kompilatora
'Identyfikator': pole bitowe nie może mieć operatora pośredniego  
  
 Pole bitowe został zadeklarowany jako wskaźnik, co jest niedozwolone.  
  
 Poniższy przykład generuje C2033:  
  
```  
// C2033.cpp  
struct S {  
   int *b : 1;  // C2033  
};  
```  
  
 Możliwe rozwiązanie:  
  
```  
// C2033b.cpp  
// compile with: /c  
struct S {  
   int b : 1;  
};  
```