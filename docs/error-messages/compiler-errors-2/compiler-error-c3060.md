---
title: C3060 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3060
dev_langs:
- C++
helpviewer_keywords:
- C3060
ms.assetid: 6282bb92-0546-4b59-9435-d3840bf93bdb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c443517edb26258f91497a4d82fcfd7ff26893d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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