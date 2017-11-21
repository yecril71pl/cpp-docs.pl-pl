---
title: "C2334 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2334
dev_langs: C++
helpviewer_keywords: C2334
ms.assetid: 36142855-e00b-4bbf-80f5-a301edeff46e
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b31ba4a8a5711fcdfbfca725938beb9afdf4301c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2334"></a>C2334 błąd kompilatora
nieoczekiwane tokeny poprzedniego ": lub {"; Pomijanie treści widocznych funkcji  
  
 Poniższy przykład generuje C2334. Ten błąd występuje po błędzie C2059:  
  
```  
// C2334.cpp  
// compile with: /c  
// C2059 expected  
struct s1 {  
   s1   {}   // C2334  
   s1() {}   // OK  
};  
```