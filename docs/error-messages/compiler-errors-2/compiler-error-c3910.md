---
title: "C3910 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3910
dev_langs: C++
helpviewer_keywords: C3910
ms.assetid: cfcbe620-b463-463b-95ea-2d60ad33ebb5
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7a1bae6f59e48f1294e657f35f7dae8ac9e937d4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3910"></a>C3910 błąd kompilatora
"event": należy zdefiniować element członkowski "method"  
  
 Zdarzenie zostało zdefiniowane, ale nie zawiera metodę dostępu określonych, wymaganych.  
  
 Aby uzyskać więcej informacji, zobacz [zdarzeń](../../windows/event-cpp-component-extensions.md).  
  
 Poniższy przykład generuje C3910:  
  
```  
// C3910.cpp  
// compile with: /clr /c  
delegate void H();  
ref class X {  
   event H^ E {  
      // uncomment the following lines  
      // void add(H^) {}  
      // void remove( H^ h ) {}  
      // void raise( ) {}  
   };   // C3910  
  
   event H^ E2; // OK data member  
};  
```