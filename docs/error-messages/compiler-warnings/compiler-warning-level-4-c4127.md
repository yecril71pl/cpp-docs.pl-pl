---
title: Kompilator ostrzeżenie (poziom 4) C4127 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/13/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4127
dev_langs:
- C++
helpviewer_keywords:
- C4127
ms.assetid: f59ded9e-5227-45bd-ac43-2aa861581363
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1bfd913b95b84d8425649476649f9bffa6163141
ms.sourcegitcommit: 87d317ac62620c606464d860aaa9e375a91f4c99
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45601525"
---
# <a name="compiler-warning-level-4-c4127"></a>Kompilator ostrzeżenie (poziom 4) C4127

> wyrażenie warunkowe jest stałą

## <a name="remarks"></a>Uwagi

Wyrażenie kontrolujące `if` instrukcji lub `while` pętli, daje w wyniku stałej. Ze względu na ich wspólne użycie idiomatyczną, począwszy od programu Visual Studio 2015 update 3, stałe prosta, taką jak 1 lub `true` nie wyzwalają ostrzeżenie, chyba że są one wynik operacji w wyrażeniu.

Jeśli wyrażenie kontrolujące `while` pętli jest stałą, ponieważ pętli kończy działanie w środku, rozważ zastąpienie `while` pętli z `for` pętli. Można pominąć inicjowanie, test zakończenia i pętli z przyrostem `for` pętli, która powoduje, że pętla nieskończony, podobnie jak `while(1)`, i może wyjście z pętli z treści `for` instrukcji.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje dwa sposoby C4127 jest generowany i przedstawia sposób użycia dla pętli uniknąć ostrzeżenia:

```cpp
// C4127.cpp  
// compile with: /W4  
#include <stdio.h>  
int main() {  
   if (true) {}           // OK in VS2015 update 3 and later
   if (1 == 1) {}         // C4127
   while (42) { break; }  // C4127

   // OK
   for ( ; ; ) {
      printf("test\n");
      break;
   }
}
```