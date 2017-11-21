---
title: "C2952 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2952
dev_langs: C++
helpviewer_keywords: C2952
ms.assetid: a40e18a2-d02c-4511-854f-6c6fd6789a1a
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7d492348171e746540d6cdda6252c325add3692f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2952"></a>C2952 błąd kompilatora
"deklaracją": lista parametrów szablonu brak deklaracji typu  
  
 Deklaracja szablonu został niewłaściwie sformatowany.  
  
 Poniższy przykład generuje C2952:  
  
```  
// C2952.cpp  
// compile with: /c  
template <class T>  
struct S {  
   template <class T1>  
   struct S1 {  
      void f();  
   };  
};  
  
template <class T> void S<T>::S1<T>::f() {}   // C2952  
  
// OK  
template <class T>  
template <class T1>  
void S<T>::S1<T1>::f() {}  
```  
  
 C2952 może również wystąpić, gdy użycie typów ogólnych:  
  
```  
// C2952b.cpp  
// compile with: /clr /c  
generic <class T>   
ref struct GC {  
   generic <class T1>   
   ref struct GC1 {  
      void f();  
   };  
};  
  
generic <class T> void GC<T>::GC1<T>::f() {}   // C2952  
  
// OK  
generic <class T>  
generic <class T1>  
void GC<T>::GC1<T1>::f() {}  
```