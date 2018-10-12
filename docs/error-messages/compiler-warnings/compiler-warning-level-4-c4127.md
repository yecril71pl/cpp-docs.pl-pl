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
ms.openlocfilehash: 80f831d527e918fce0551f6a1336fd2fe994917d
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2018
ms.locfileid: "49161284"
---
# <a name="compiler-warning-level-4-c4127"></a>Kompilator ostrzeżenie (poziom 4) C4127

> wyrażenie warunkowe jest stałą

## <a name="remarks"></a>Uwagi

Wyrażenie kontrolujące **Jeśli** instrukcji lub **podczas** pętli, daje w wyniku stałej. Ze względu na ich wspólne użycie idiomatyczną, począwszy od programu Visual Studio 2015 update 3, stałe prosta, taką jak 1 lub **true** nie wyzwalają ostrzeżenie, chyba że są one wynik operacji w wyrażeniu.

Jeśli wyrażenie kontrolujące **podczas** pętli jest stałą, ponieważ pętli kończy działanie w środku, rozważ zastąpienie **podczas** pętli z **dla** pętli. Można pominąć inicjowanie, test zakończenia i pętli z przyrostem **dla** pętli, która powoduje, że pętla nieskończony, podobnie jak `while(1)`, i może wyjście z pętli z treści **dla** Instrukcja.

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