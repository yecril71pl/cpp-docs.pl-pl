---
title: "C3152 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3152
dev_langs: C++
helpviewer_keywords: C3152
ms.assetid: 4ee6e2cd-5d19-4b73-833d-765c35797e4b
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 222a45a8a8820c426902ef3584a3663103b63fa2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3152"></a>C3152 błąd kompilatora
"skonstruować": "— słowo kluczowe" można stosować do klasy, struktury lub wirtualnej funkcji członkowskiej  
  
 Niektóre słowa kluczowe może być stosowany tylko do klasy C++.  
  
 Poniższy przykład generuje C3152 i pokazuje, jak rozwiązywanie problemu:  
  
```  
// C3152.cpp  
// compile with: /clr /c  
ref class C {  
   int (*pfn)() sealed;   // C3152  
   virtual int g() sealed;   // OK  
};  
```  
