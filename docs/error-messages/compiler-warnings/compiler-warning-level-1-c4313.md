---
title: Kompilator ostrzeżenie (poziom 1) C4313
ms.date: 11/04/2016
f1_keywords:
- C4313
helpviewer_keywords:
- C4313
ms.assetid: bcf64191-e2cf-452e-97b4-423fcec2d07c
ms.openlocfilehash: 774af2d5d29112d56adf97e22d1bdd758a816ef1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50555713"
---
# <a name="compiler-warning-level-1-c4313"></a>Kompilator ostrzeżenie (poziom 1) C4313

'Funkcja': 'specyfikatora formatu"w formacie ciągu powoduje konflikt z numerem argumentu typu"type"

Istnieje konflikt między z formatem określonym i wartość, która kończy się sukcesem. Na przykład został przekazany parametr 64-bitowych do %d niekwalifikowanej specyfikator formatu, który oczekuje, że parametr 32-bitową liczbę całkowitą. To ostrzeżenie działa tylko wtedy, gdy kod jest kompilowany dla celów 64-bitowych.

## <a name="example"></a>Przykład

Poniższy przykładowy kod generuje C4313, gdy jest ona skompilowana dla elementu docelowego 64-bitowych.

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