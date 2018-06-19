---
title: C2723 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2723
dev_langs:
- C++
helpviewer_keywords:
- C2723
ms.assetid: 86925601-2297-4cfd-94e2-2caf27c474c4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 01476218683205d0fb06e81847cfe9727b733158
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33233787"
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