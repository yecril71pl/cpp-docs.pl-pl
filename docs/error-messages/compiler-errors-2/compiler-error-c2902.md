---
title: "C2902 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2902
dev_langs: C++
helpviewer_keywords: C2902
ms.assetid: 89d78d0e-78e5-4c2c-a0f9-a60110e9395e
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2daad775980c881bb1400c695015bd094ffc14cf
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2902"></a>C2902 błąd kompilatora
'token': nieoczekiwany token następujący "szablon", oczekiwano identyfikatora  
  
 Token po słowie kluczowym `template` nie jest identyfikatorem.  
  
 Poniższy przykład generuje C2902:  
  
```  
// C2902.cpp  
// compile with: /c  
namespace N {  
   template<class T> class X {};  
   class Y {};  
}  
void g() {  
   N::template + 1;   // C2902  
}  
  
void f() {  
   N::template X<int> x1;   // OK  
}  
```  
  
 C2902 może również wystąpić, gdy użycie typów ogólnych:  
  
```  
// C2902b.cpp  
// compile with: /clr /c  
namespace N {  
   generic<class T> ref class GC {};  
}  
  
void f() {  
   N::generic + 1;   // C2902  
   N::generic GC<int>^ x;  
}  
```