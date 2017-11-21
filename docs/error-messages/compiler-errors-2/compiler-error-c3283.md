---
title: "C3283 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3283
dev_langs: C++
helpviewer_keywords: C3283
ms.assetid: c51d912c-cde3-4928-904e-26734c8954ce
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 94b1028f19cd5ca8b490e3247d0f55cff36bb19a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3283"></a>C3283 błąd kompilatora
'type': interfejs nie może posiadać konstruktora wystąpień  
  
 Środowisko CLR [interfejsu](../../windows/interface-class-cpp-component-extensions.md) nie może posiadać konstruktora wystąpień.  Konstruktor statyczny jest dozwolone.  
  
 Poniższy przykład generuje C3283:  
  
```  
// C3283.cpp  
// compile with: /clr  
interface class I {  
   I();   // C3283  
};  
```  
  
 Możliwe rozwiązanie:  
  
```  
// C3283b.cpp  
// compile with: /clr /c  
interface class I {  
   static I(){}  
};  
```