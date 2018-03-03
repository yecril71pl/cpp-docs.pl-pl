---
title: "Kompilatora (poziom 1) ostrzeżenie C4313 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4313
dev_langs:
- C++
helpviewer_keywords:
- C4313
ms.assetid: bcf64191-e2cf-452e-97b4-423fcec2d07c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1b90fe384ac3396e73eb2fc69aab3a6d48552adf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4313"></a>Kompilator C4313 ostrzegawcze (poziom 1)
"Funkcja": "specyfikatorze formatu" w formacie ciągu powoduje konflikt z numer argumentu typu "type"  
  
 Występuje konflikt między określony format i wartość, która jest przekazywany. Na przykład został przekazany parametr 64-bitowej do niekwalifikowanych %d specyfikatora formatu, który oczekuje parametru 32-bitową liczbę całkowitą. To ostrzeżenie działa tylko wtedy, gdy kod jest kompilowany dla celów 64-bitowych.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu generuje C4313, gdy jest on skompilowany dla elementu docelowego 64-bitowych.  
  
```  
// C4313.cpp  
// Compile by using: cl /W1 C4313.cpp  
#include <stdio.h>  
int main() {  
   int * pI = 0;  
   printf("%d", pI);   // C4313 on 64-bit platform code  
   // Try one of the following lines instead:  
   // printf("%p\n", pI);  
   // printf("%Id\n", pI);   // %I64d expects 64-bits of information  
}  
```