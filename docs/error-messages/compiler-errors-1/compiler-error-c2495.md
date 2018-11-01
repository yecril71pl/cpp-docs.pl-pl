---
title: Błąd kompilatora C2495
ms.date: 11/04/2016
f1_keywords:
- C2495
helpviewer_keywords:
- C2495
ms.assetid: bb7066fe-3549-4901-97e4-157f3c04dd57
ms.openlocfilehash: 83a0359fce175b12dd18e2500d63d7a86bed9f0b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50436039"
---
# <a name="compiler-error-c2495"></a>Błąd kompilatora C2495

'Identyfikator': "nothrow" może być stosowane tylko do deklaracji lub definicji funkcji

[Nothrow](../../cpp/nothrow-cpp.md) atrybutów rozszerzonych można zastosować do deklaracji lub definicji tylko funkcji.

Poniższy przykład spowoduje wygenerowanie C2495:

```
// C2495.cpp
// compile with: /c
__declspec(nothrow) class X {   // C2495
   int m_data;
} x;

__declspec(nothrow) void test();   // OK
```