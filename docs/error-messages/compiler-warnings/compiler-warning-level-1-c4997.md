---
title: "Kompilatora (poziom 1) ostrzeżenie C4997 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4997
dev_langs: C++
helpviewer_keywords: C4997
ms.assetid: d39678fd-0c1a-4104-8a45-9e3f20de0407
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: cb9c3c0d2b48db5676c8510c75ef9e6bee42a160
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4997"></a>Kompilator C4997 ostrzegawcze (poziom 1)
"class": klasa coclass nie implementuje interfejsu COM lub pseudointerfejsu  
  
 Klasy oznaczonej [coclass](../../windows/coclass.md) atrybutu nie implementuje interfejsu.  
  
 Poniższy przykład generuje C4997:  
  
```  
// C4997.cpp  
// compile with: /WX  
// to resolve this C4997, uncomment all code  
#include <objbase.h>  
  
[ object ]  
__interface I {  
   HRESULT func();  
};  
  
[ coclass ]  
struct C /*: I*/ {  
   /*  
   HRESULT func() {  
      return S_OK;  
   }  
   */  
};   // C4997  
```