---
title: C2004 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2004
dev_langs:
- C++
helpviewer_keywords:
- C2004
ms.assetid: d81526dd-3a00-4593-87b0-d910d3d29bca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d4030ea3c82c1a893ebf35903d3fbc362c594282
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2004"></a>C2004 błąd kompilatora
Oczekiwano defined(id)  
  
 Identyfikator muszą być umieszczone w nawiasach po słowie kluczowym preprocesora.  
  
 Ten błąd może być również generowany w wyniku pracy zgodność kompilatora, która została wykonana dla programu Visual Studio .NET 2003: brak nawiasów w dyrektywie preprocesora. Jeśli brakuje nawiasu zamykającego dyrektywy preprocesora, kompilator wygeneruje błąd.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C2004:  
  
```  
// C2004.cpp  
// compile with: /DDEBUG  
#include <stdio.h>  
  
int main()   
{  
    #if defined(DEBUG   // C2004  
        printf_s("DEBUG defined\n");  
    #endif  
}  
```  
  
## <a name="example"></a>Przykład  
 Możliwe rozwiązanie:  
  
```  
// C2004b.cpp  
// compile with: /DDEBUG  
#include <stdio.h>  
  
int main()   
{  
    #if defined(DEBUG)  
        printf_s("DEBUG defined\n");  
    #endif  
}  
```