---
title: "C3060 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3060
dev_langs: C++
helpviewer_keywords: C3060
ms.assetid: 6282bb92-0546-4b59-9435-d3840bf93bdb
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 528ce6f8b94d73acde2a92412c6f3578dd83b4bd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3060"></a>C3060 błąd kompilatora
"członek": funkcja zaprzyjaźniona nie może być zdefiniowana wewnątrz klasy przy użyciu nazwy kwalifikowanej (go może być tylko zadeklarowana)  
  
 Funkcja zaprzyjaźniona został zdefiniowany przy użyciu nazwy kwalifikowanej, co jest niedozwolone.  
  
 Poniższy przykład generuje C3060:  
  
```  
// C3060.cpp  
class A {  
public:  
   void func();  
};  
  
class C {  
public:  
   friend void A::func() { }   // C3060  
   // Try the following line and the out of class definition:  
   // friend void A::func();  
};  
  
// void A::func(){}  
```