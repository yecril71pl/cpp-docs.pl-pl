---
title: "Kompilatora (poziom 1) ostrzeżenie C4033 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4033
dev_langs: C++
helpviewer_keywords: C4033
ms.assetid: 189a9ec3-ff6d-49dd-b9b2-530b28bbb7c9
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a215fef10e75a3686cbb04121d419cc0861d4a1e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4033"></a>Kompilator C4033 ostrzegawcze (poziom 1)
"function" musi zwracać wartość  
  
 Funkcja nie zwraca wartości. Niezdefiniowana wartość jest zwracana.  
  
 Funkcje używające `return` bez wartości zwracanej musi być zadeklarowany jako typ `void`.  
  
 Ten błąd jest dla kodu języka C.  
  
 Poniższy przykład generuje C4033:  
  
```  
// C4033.c  
// compile with: /W1 /LD  
int test_1(int x)   // C4033 expected  
{  
   if (x)  
   {  
      return;   // C4033  
   }  
}  
```