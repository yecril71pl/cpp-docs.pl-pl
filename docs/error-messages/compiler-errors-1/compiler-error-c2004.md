---
title: Błąd kompilatora C2004
ms.date: 11/04/2016
f1_keywords:
- C2004
helpviewer_keywords:
- C2004
ms.assetid: d81526dd-3a00-4593-87b0-d910d3d29bca
ms.openlocfilehash: fb100d977188cd3a7d5b0ebbb3e29b53942871dc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50452022"
---
# <a name="compiler-error-c2004"></a>Błąd kompilatora C2004

oczekiwane "określone(ID)"

Identyfikator musi znajdować się w nawiasach, po słowie kluczowym preprocesora.

Ten błąd może być też wygenerowany w wyniku pracy zgodności kompilatora, która została wykonana dla Visual Studio .NET 2003: Brak nawiasu w dyrektywy preprocesora. Jeśli brakuje nawiasu zamykającego dyrektywy preprocesora, kompilator wygeneruje błąd.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C2004:

```
// C2004.cpp
// compile with: /DDEBUG
#include <stdio.h>

int main()
{
    #if defined(DEBUG   // C2004
        printf_s("DEBUG defined\n");
    #endif
}
```

## <a name="example"></a>Przykład

Możliwe rozwiązanie:

```
// C2004b.cpp
// compile with: /DDEBUG
#include <stdio.h>

int main()
{
    #if defined(DEBUG)
        printf_s("DEBUG defined\n");
    #endif
}
```