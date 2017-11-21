---
title: "C2254 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2254
dev_langs: C++
helpviewer_keywords: C2254
ms.assetid: 49bb3d7e-3bdf-4af6-937c-fa627be412a9
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: cf8eb577b027b1d6cd4b62b28cb0da785349091f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2254"></a>C2254 błąd kompilatora
"Funkcja": czysty specyfikator lub abstrakcyjny specyfikator override nie dozwolony dla funkcji zaprzyjaźnionej  
  
 A `friend` jest określony jako czysty `virtual`.  
  
 Poniższy przykład generuje C2254:  
  
```  
// C2254.cpp  
// compile with: /c  
class A {  
public:  
   friend void func1() = 0;   // C2254, func1 is friend  
   void virtual func2() = 0;   // OK, pure virtual  
   friend void func3();   // OK, friend not virtual nor pure  
};  
  
void func1() {};  
void func3() {};  
```