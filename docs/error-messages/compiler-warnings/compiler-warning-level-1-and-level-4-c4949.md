---
title: Kompilator ostrzeżenie (poziom 1 i 4) C4949
ms.date: 11/04/2016
f1_keywords:
- C4949
helpviewer_keywords:
- C4949
ms.assetid: 34f45a05-c115-49cb-9f67-0bd4f0735d9b
ms.openlocfilehash: 8050edbd7a653776d046bc7b4155fd43094d9a5d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50515939"
---
# <a name="compiler-warning-level-1-and-level-4-c4949"></a>Kompilator ostrzeżenie (poziom 1 i 4) C4949

dyrektywy pragma "managed" i "unmanaged" mają znaczenie, tylko wtedy, gdy skompilowano z opcją "/ clr [: option]"

Kompilator ignoruje [zarządzane](../../preprocessor/managed-unmanaged.md) i niezarządzane pragm, jeśli kod źródłowy nie jest skompilowany przy użyciu [/CLR](../../build/reference/clr-common-language-runtime-compilation.md). To ostrzeżenie ma charakter informacyjny.

Poniższy przykład spowoduje wygenerowanie C4949:

```
// C4949.cpp
// compile with: /LD /W1
#pragma managed   // C4949
```

Gdy **niezarządzanych #pragma** jest używany bez **/CLR**, C4949 to ostrzeżenie poziom 4.

Poniższy przykład spowoduje wygenerowanie C4949:

```
// C4949b.cpp
// compile with: /LD /W4
#pragma unmanaged   // C4949
```