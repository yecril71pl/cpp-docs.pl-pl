---
title: "C2723 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2723
dev_langs:
- C++
helpviewer_keywords:
- C2723
ms.assetid: 86925601-2297-4cfd-94e2-2caf27c474c4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 587dd742a089a0eddc416e59563cd1e0707e662b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2723"></a>C2723 błąd kompilatora
"Funkcja": specyfikator "specyfikatora" jest niedozwolony w definicji funkcji  
  
 Specyfikator nie może występować w definicji funkcji poza deklaracją klasy. `virtual` Specyfikator można określić tylko w deklaracji funkcji elementu członkowskiego w deklaracji klasy.  
  
 Poniższy przykład generuje C2723 i pokazuje, jak rozwiązywanie problemu:  
  
```  
// C2723.cpp  
struct X {  
   virtual void f();  
   virtual void g();  
};  
  
virtual void X::f() {}   // C2723  
  
// try the following line instead  
void X::g() {}  
```