---
title: C2698 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2698
dev_langs:
- C++
helpviewer_keywords:
- C2698
ms.assetid: 3ebfe395-c20b-4c56-9980-ca9ed8653382
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7c466e39702f1e408ad96d79c16c4a5953fa373f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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