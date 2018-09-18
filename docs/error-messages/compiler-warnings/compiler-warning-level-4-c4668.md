---
title: Kompilator ostrzeżenie (poziom 4) C4668 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4668
dev_langs:
- C++
helpviewer_keywords:
- C4668
ms.assetid: c6585460-bc4a-4a15-9242-4cbfce53c961
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c960eb2cc79298977c8d7c91808b0a5492d05758
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46074011"
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