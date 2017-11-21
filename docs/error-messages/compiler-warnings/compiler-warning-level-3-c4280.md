---
title: "Kompilatora (poziom 3) ostrzeżenie C4280 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4280
dev_langs: C++
helpviewer_keywords: C4280
ms.assetid: 153fb639-3ee1-4fee-baf9-71420abcf3f6
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3733b8f95f92b4dd8e15e3456be3b19959e323b1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-3-c4280"></a>Kompilator C4280 ostrzegawcze (poziom 3)
"operator ->" był Auto rekurencyjny za pośrednictwem typu "type"  
  
 Kod niepoprawnie umożliwia **operator ->** można wywołać się.  
  
 Poniższy przykład generuje C4280:  
  
```  
// C4280.cpp  
// compile with: /W3 /WX  
struct A  
{  
   int z;  
   A& operator ->();  
};  
  
void f(A y)  
{  
   int i = y->z; // C4280  
}  
```