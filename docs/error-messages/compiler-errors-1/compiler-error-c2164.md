---
title: Błąd kompilatora C2164
ms.date: 11/04/2016
f1_keywords:
- C2164
helpviewer_keywords:
- C2164
ms.assetid: 55df5024-68a8-45a8-ae6c-e6dba35318a2
ms.openlocfilehash: 3b1c7a94dfca1c2767e14f96204ecda670c8a586
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62174825"
---
# <a name="compiler-error-c2164"></a>Błąd kompilatora C2164

'Funkcja': wewnętrzna funkcja nie jest zadeklarowana

`intrinsic` Pragma używa niezadeklarowanego funkcji (występuje tylko w przypadku **/Oi**). Lub jeden funkcje wewnętrzne kompilatora został użyty bez uwzględniania jej pliku nagłówka.

Poniższy przykład spowoduje wygenerowanie C2164:

```
// C2164.c
// compile with: /c
// processor: x86
// Uncomment the following line to resolve.
// #include "xmmintrin.h"
void b(float *p) {
   _mm_load_ss(p);   // C2164
}
```