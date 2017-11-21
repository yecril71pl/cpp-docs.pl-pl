---
title: Kompilator C4949 ostrzegawcze (poziom 1 i 4) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4949
dev_langs: C++
helpviewer_keywords: C4949
ms.assetid: 34f45a05-c115-49cb-9f67-0bd4f0735d9b
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 241e0295b16ae350cec213bf25b93f7ad72a0808
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-and-level-4-c4949"></a>Kompilator C4949 ostrzegawcze (poziom 1 i 4)
dyrektywy pragma "managed" i "unmanaged" mają znaczenie, tylko wtedy, gdy skompilowano z opcją "/ clr [: option]"  
  
 Kompilator ignoruje [zarządzane](../../preprocessor/managed-unmanaged.md) i niezarządzanych pragm, jeśli kod źródłowy nie jest skompilowana przy użyciu [/CLR](../../build/reference/clr-common-language-runtime-compilation.md). To ostrzeżenie ma charakter informacyjny.  
  
 Poniższy przykład generuje C4949:  
  
```  
// C4949.cpp  
// compile with: /LD /W1  
#pragma managed   // C4949  
```  
  
 Gdy **#pragma niezarządzanych** jest używana bez **/CLR**, C4949 to ostrzeżenie poziom 4.  
  
 Poniższy przykład generuje C4949:  
  
```  
// C4949b.cpp  
// compile with: /LD /W4  
#pragma unmanaged   // C4949  
```