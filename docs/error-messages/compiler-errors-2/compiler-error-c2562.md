---
title: "C2562 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2562
dev_langs: C++
helpviewer_keywords: C2562
ms.assetid: 2c41e511-9952-4b98-9976-6b1523613e1b
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: bcd98e241abd5cfd8cfce16224069470493d89b5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2562"></a>C2562 błąd kompilatora
"identyfikator": "void" funkcji zwracającej wartość  
  
 Funkcja jest zadeklarowany jako `void` , ale zwraca wartość.  
  
 Przyczyną tego błędu może być prototypu Niepoprawna funkcja.  
  
 Ten błąd może można naprawić, jeśli w deklaracji funkcji można określić typ zwracany.  
  
 Poniższy przykład generuje C2562:  
  
```  
// C2562.cpp  
// compile with: /c  
void testfunc() {  
   int i;  
   return i;   // C2562 delete the return to resolve  
}  
```