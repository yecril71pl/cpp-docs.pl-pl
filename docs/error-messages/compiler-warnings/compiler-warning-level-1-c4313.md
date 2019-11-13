---
title: Ostrzeżenie kompilatora (poziom 1) C4313
ms.date: 11/04/2016
f1_keywords:
- C4313
helpviewer_keywords:
- C4313
ms.assetid: bcf64191-e2cf-452e-97b4-423fcec2d07c
ms.openlocfilehash: 4000ba2254c868bf9959a6f0fb6f8e76255f7590
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966080"
---
# <a name="compiler-warning-level-1-c4313"></a>Ostrzeżenie kompilatora (poziom 1) C4313

"Function": "format specyfikatora" w ciągu formatu powoduje konflikt z numerem argumentu typu "Type"

Występuje konflikt między określonym formatem a wartością przekazywaną przez użytkownika. Na przykład przeszedł parametr 64-bitowy do niekwalifikowanego specyfikatora formatu% d, który oczekuje parametru 32-bit Integer. To ostrzeżenie jest stosowane tylko wtedy, gdy kod jest kompilowany dla elementów docelowych 64-bitowych.

## <a name="example"></a>Przykład

Poniższy przykładowy kod generuje C4313, gdy jest kompilowany dla elementu docelowego 64-bitowego.

```cpp
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