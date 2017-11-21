---
title: "C2474 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2474
dev_langs: C++
helpviewer_keywords: C2474
ms.assetid: 64e6c61e-6e77-480e-bcf0-b30a2fc482ac
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0630072032d69b5f936174945e366b20556a32d9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2474"></a>C2474 błąd kompilatora
"— słowo kluczowe": Brak sąsiadującego średnika, mogą być słowo kluczowe lub identyfikator.  
  
 Kompilator Oczekiwano znalezienia średnikiem i nie może określić Twoich zamiarów. Dodaj średnik, aby rozwiązać ten problem.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C2474.  
  
```  
// C2474.cpp  
// compile with: /clr /c  
  
ref class A {  
   ref class B {}  
   property int i;   // C2474 error  
};  
  
// OK  
ref class B {  
   ref class D {};  
   property int i;  
};  
  
ref class E {  
   ref class F {} property;   
   int i;  
};  
```