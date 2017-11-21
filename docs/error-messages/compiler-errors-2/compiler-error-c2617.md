---
title: "C2617 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2617
dev_langs: C++
helpviewer_keywords: C2617
ms.assetid: d6a435d2-7d95-4dbf-ad4a-abe4744f63e8
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5e3272cb883469abbad5ee42538a7334ecd73d62
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2617"></a>C2617 błąd kompilatora
"Funkcja": niespójna instrukcja return  
  
 Określona funkcja nie ma zadeklarowany typ zwracany i poprzedniego zwracać instrukcji nie podano wartości.  
  
 Poniższy przykład generuje C2617:  
  
```  
// C2617.cpp  
int i;  
func() {   // no return type prototype  
   if( i ) return;   // no return value  
   else return( 1 );   // C2617 detected on this line  
}  
```  
  
 Możliwe rozwiązanie:  
  
```  
// C2617b.cpp  
// compile with: /c  
int i;  
int MyF() {  
   if (i)  
      return 0;  
   else   
      return (1);  
}  
```