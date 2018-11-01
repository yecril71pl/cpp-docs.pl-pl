---
title: Kompilator ostrzeżenie (poziom 4) C4668
ms.date: 11/04/2016
f1_keywords:
- C4668
helpviewer_keywords:
- C4668
ms.assetid: c6585460-bc4a-4a15-9242-4cbfce53c961
ms.openlocfilehash: 11d96941a1efddde87068af8829e24259f2fa312
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50529977"
---
# <a name="compiler-warning-level-4-c4668"></a>Kompilator ostrzeżenie (poziom 4) C4668

'symbol' nie jest zdefiniowany jako makro preprocesora, zastępowanie przez '0' dla 'dyrektywy'

Symbol, który nie został zdefiniowany był używany za pomocą dyrektywy preprocesora. Symbol ocenia się na wartość false. Aby zdefiniować symbol, można użyć albo [#define — dyrektywa](../../preprocessor/hash-define-directive-c-cpp.md) lub [/D](../../build/reference/d-preprocessor-definitions.md) — opcja kompilatora.

To ostrzeżenie jest domyślnie wyłączona. Zobacz [kompilatora ostrzeżenia, są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Aby uzyskać więcej informacji.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4668:

```
// C4668.cpp
// compile with: /W4
#include <stdio.h>

#pragma warning (default : 4668)   // turn warning on

int main()
{
    #if q   // C4668, q is not defined
        printf_s("defined");
    #else
        printf_s("undefined");
    #endif
}
```