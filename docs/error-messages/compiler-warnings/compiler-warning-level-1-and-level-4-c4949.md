---
title: Kompilator ostrzeżenie (poziom 1 i 4) C4949 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4949
dev_langs:
- C++
helpviewer_keywords:
- C4949
ms.assetid: 34f45a05-c115-49cb-9f67-0bd4f0735d9b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f806912188ada3a4f97f0b1500e811d1271f40fe
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46077311"
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