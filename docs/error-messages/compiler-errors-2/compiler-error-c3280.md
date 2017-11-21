---
title: "C3280 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3280
dev_langs: C++
helpviewer_keywords: C3280
ms.assetid: 86dc5bbc-8818-4786-a728-9334268d308b
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4534ac1df55ed5e0810cd0a8d5ce54a5081b929e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3280"></a>C3280 błąd kompilatora
"class": funkcja członkowska typu zarządzanego nie można skompilować jako funkcji niezarządzanej  
  
 Zarządzany element członkowski klasy, które funkcje nie można skompilować jako funkcji niezarządzanej.  
  
 Poniższy przykład generuje C3280:  
  
```  
// C3280_2.cpp  
// compile with: /clr  
ref struct A {  
   void func();  
};  
  
#pragma managed(push,off)  
  
void A::func()   // C3280  
{  
}  
  
#pragma managed(pop)  
```  
