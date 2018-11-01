---
title: Kompilator ostrzeżenie (poziom 1) C4391
ms.date: 11/04/2016
f1_keywords:
- C4391
helpviewer_keywords:
- C4391
ms.assetid: 95c6182c-fae9-4174-8f7b-98aa352e68ca
ms.openlocfilehash: d9d1cebe08a6a163d76271ab001ec91b7cee82a2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50567131"
---
# <a name="compiler-warning-level-1-c4391"></a>Kompilator ostrzeżenie (poziom 1) C4391

"podpis": nieprawidłowy typ zwracany dla wewnętrznej funkcji, oczekiwano "type"

Deklaracja funkcji wewnętrzne polecenie kompilatora ma niewłaściwy typ zwracany. Obraz wynikowy może nie działać poprawnie.

Aby usunąć to ostrzeżenie, popraw deklarację albo usuń deklarację i po prostu #include do odpowiedniego pliku nagłówka.

Poniższy przykład spowoduje wygenerowanie C4391:

```
// C4391.cpp
// compile with: /W1
// processor: x86
// uncomment the following line and delete the line that
// generated the warning to resolve
// #include "xmmintrin.h"

#ifdef  __cplusplus
extern "C" {
#endif

extern void _mm_load_ss(float *p);   // C4391

#ifdef  __cplusplus
}
#endif

int main()
{
}
```