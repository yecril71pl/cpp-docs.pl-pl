---
title: Błąd kompilatora C2013
ms.date: 11/04/2016
f1_keywords:
- C2013
helpviewer_keywords:
- C2013
ms.assetid: 6b5c955c-53da-48ee-8533-64ef5b905173
ms.openlocfilehash: b279202b8b32197a99d230040207aa50bc100495
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50618481"
---
# <a name="compiler-error-c2013"></a>Błąd kompilatora C2013

Brak ">"

`#include` Dyrektywy nie posiada zamykającego nawiasu ostrego. Dodaj nawias zamykający, aby naprawić błąd.

Poniższy przykład spowoduje wygenerowanie C2013:

```
// C2013.cpp
#include <stdio.h    // C2013
```

Możliwe rozwiązanie:

```
// C2013b.cpp
// compile with: /c
#include <stdio.h>
```