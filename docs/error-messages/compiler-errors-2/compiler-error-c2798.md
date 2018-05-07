---
title: C2798 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2798
dev_langs:
- C++
helpviewer_keywords:
- C2798
ms.assetid: fb0cd861-b228-4f81-8090-e28344a727e0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: de30a19a2a27cde991cfce0ca061ce6f5447f033
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2798"></a>C2798 błąd kompilatora
"super::member" jest niejednoznaczny  
  
 Wiele dziedziczone struktury zawierają element członkowski odwołania z [super](../../cpp/super.md). Błąd można rozwiązać przez:  
  
-   Usuwanie z listy dziedziczenia d. B1 lub B2  
  
-   Zmiana nazwy elementu członkowskiego danych w B1 lub B2.  
  
 Poniższy przykład generuje C2798:  
  
```  
// C2798.cpp  
struct B1 {  
   int i;  
};  
  
struct B2 {  
   int i;  
};  
  
struct D : B1, B2 {  
   void g() {  
      __super::i = 4; // C2798  
   }  
};  
```