---
title: "Kompilatora (poziom 4) ostrzeżenie C4515 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4515
dev_langs: C++
helpviewer_keywords: C4515
ms.assetid: 167b5177-3f89-418b-b6c8-7de634f6b28f
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1fff014d478812f2924601ad43f05d1badbd76ae
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4515"></a>Kompilator C4515 ostrzegawcze (poziom 4)
"namespace": przestrzeń nazw używa sama siebie  
  
 Przestrzeń nazw jest używana rekursywnie.  
  
 Poniższy przykład generuje C4515:  
  
```  
// C4515.cpp  
// compile with: /W4  
namespace A  
{  
   using namespace A; // C4515  
}  
  
int main()  
{  
}  
```