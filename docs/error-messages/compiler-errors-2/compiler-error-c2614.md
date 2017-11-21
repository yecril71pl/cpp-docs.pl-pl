---
title: "C2614 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2614
dev_langs: C++
helpviewer_keywords: C2614
ms.assetid: a550c1d5-8718-4e17-a888-b2619e00fe11
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 077762fef5474b3761c504224c58de83d82bdb12
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2614"></a>C2614 błąd kompilatora
"class1": niedozwolona Inicjalizacja elementu członkowskiego: "class2" nie jest podstawowym lub elementu członkowskiego  
  
 Tylko element członkowski lub klas podstawowych może występować na liście inicjowania dla klasy lub struktury.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C2614.  
  
```  
// C2614.cpp  
// compile with: /c  
struct A {  
   int i;  
   A( int ia ) : B( i ) {};   // C2614 B is not a member of A  
};  
  
struct A2 {  
   int B;  
   int i;  
   A2( int ia ) : B( i ) {};   // OK  
};  
```