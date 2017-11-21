---
title: "C3903 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3903
dev_langs: C++
helpviewer_keywords: C3903
ms.assetid: cf47d7ad-a3bd-4f75-a253-71586e7a3be6
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 59dcfa1b7829b8367fdefb3fd89f5b9f1d5a7897
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3903"></a>C3903 błąd kompilatora
"właściwość": jest nie ustawiono lub get, metoda  
  
 Właściwość musi mieć co najmniej `get` lub `set` metody. Aby uzyskać więcej informacji, zobacz [właściwości](../../windows/property-cpp-component-extensions.md).  
  
 Poniższy przykład generuje C3903:  
  
```  
// C3903.cpp  
// compile with: /clr  
ref class X {  
   property int P {  
      void f(int){}  
      // Add one or both of the following lines.  
      // void set(int){}  
      // int get(){return 0;}  
   };   // C3903  
  
   property double Q[,,,,] {  
      void f(){}  
      // Add one or both of the following lines.  
      // void set(int, char, int, char, double, double){}  
      // double get(int, char, int, char, double){return 1.1;}  
   }   // C3903  
};  
```