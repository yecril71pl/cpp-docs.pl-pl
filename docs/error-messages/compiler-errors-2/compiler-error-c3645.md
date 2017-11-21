---
title: "C3645 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3645
dev_langs: C++
helpviewer_keywords: C3645
ms.assetid: 346da528-ae86-4cd0-9654-f41bee26ac0d
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 43bda10ee2e4f2939061d70cfcf19da950909d03
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3645"></a>C3645 błąd kompilatora
"Funkcja": __clrcall nie można używać w funkcjach skompilowanych do natywnego kodu  
  
 Obecność niektórych słów kluczowych w funkcji spowoduje, że funkcja zestawiane na natywny.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3645.  
  
```  
// C3645.cpp  
// compile with: /clr /c  
#pragma unmanaged   
int __clrcall dog() {}   // C3645  
```