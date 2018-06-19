---
title: C2391 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2391
dev_langs:
- C++
helpviewer_keywords:
- C2391
ms.assetid: 63a9c6b9-03cc-4517-885c-bdcd048643b3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a16ed19f5cac9d6c23a3f709e40fc290223e93c7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33224768"
---
# <a name="compiler-error-c2391"></a>C2391 błąd kompilatora
"identyfikator": "friend" nie może zostać użyty podczas definicji typu  
  
 `friend` Deklaracja zawiera deklarację pełnej klasy. A `friend` deklaracji można określić funkcji członkowskiej lub specyfikatorze typu złożonego, ale nie deklaracji klasy ukończone.  
  
 Poniższy przykład generuje C2326:  
  
```  
// C2391.cpp  
// compile with: /c  
class D {   
   void func( int );   
};  
  
class A {  
   friend class B { int i; };   // C2391  
  
   // OK  
   friend class C;  
   friend void D::func(int);  
};  
```