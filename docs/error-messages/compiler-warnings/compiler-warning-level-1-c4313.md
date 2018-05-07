---
title: Kompilatora (poziom 1) ostrzeżenie C4313 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4313
dev_langs:
- C++
helpviewer_keywords:
- C4313
ms.assetid: bcf64191-e2cf-452e-97b4-423fcec2d07c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e42bd8f19ac9a70f93a26265af6e310fb51e7229
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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