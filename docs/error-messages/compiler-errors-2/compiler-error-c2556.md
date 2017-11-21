---
title: "C2556 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2556
dev_langs: C++
helpviewer_keywords: C2556
ms.assetid: fc4399ad-45b3-49fd-be1f-0b13956a595a
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6678c34022c28dccfa5920809e7b8d6db0d39546
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2556"></a>C2556 błąd kompilatora
'Identyfikator': przeciążonej funkcji różnią się tylko typem zwracanym  
  
 Funkcje przeciążone mają różne typy zwracane, ale tej samej listy parametrów. Każdy przeciążonej funkcji musi mieć różne formalnej listy parametrów.  
  
 Poniższy przykład generuje C2556:  
  
```  
// C2556.cpp  
// compile with: /c  
class C {  
   int func();  
   double func();   // C2556  
   int func(int i);   // ok parameter lists differ  
};  
```