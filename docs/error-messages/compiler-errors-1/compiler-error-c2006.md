---
title: Błąd kompilatora C2006
ms.date: 11/04/2016
f1_keywords:
- C2006
helpviewer_keywords:
- C2006
ms.assetid: caaed6f7-ceb9-4742-8820-d66657c0b04d
ms.openlocfilehash: c23f17483925f25468214165fb459db577e576fc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50475091"
---
# <a name="compiler-error-c2006"></a>Błąd kompilatora C2006

"dyrektywa" Oczekiwano nazwy pliku, znaleziono "token"

Dyrektywy, takie jak [#include](../../preprocessor/hash-include-directive-c-cpp.md) lub [#import](../../preprocessor/hash-import-directive-cpp.md) wymagają nazwy pliku. Aby naprawić błąd, upewnij się, *tokenu* jest prawidłową nazwą pliku. Ponadto umieść nazwę pliku w podwójne cudzysłowy lub nawiasy.

Poniższy przykład spowoduje wygenerowanie C2006:

```
// C2006.cpp
#include stdio.h   // C2006
```

Możliwe rozwiązanie:

```
// C2006b.cpp
// compile with: /c
#include <stdio.h>
```