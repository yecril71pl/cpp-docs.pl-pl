---
title: "C2698 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2698
dev_langs: C++
helpviewer_keywords: C2698
ms.assetid: 3ebfe395-c20b-4c56-9980-ca9ed8653382
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 654367e882b16c18cc4bd58c339d61c653dc68e9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2698"></a>C2698 błąd kompilatora
Deklaracja using dla "deklaracji 1' nie może współistnieć z istniejącą deklaracją using dla" deklaracja 2"  
  
 Po utworzeniu [za pomocą deklaracji](../../cpp/using-declaration.md) dla elementu członkowskiego danych za pomocą dowolnego deklaracja w tym samym zakresie, który używa tej samej nazwie nie jest dozwolona, ponieważ tylko funkcje mogą być przeciążone.  
  
 Poniższy przykład generuje C2698:  
  
```  
// C2698.cpp  
struct A {  
   int x;  
};  
  
struct B {  
   int x;  
};  
  
struct C : A, B {  
   using A::x;  
   using B::x;   // C2698  
}  
```