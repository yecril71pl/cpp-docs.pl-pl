---
title: Błąd kompilatora C2004
ms.date: 11/04/2016
f1_keywords:
- C2004
helpviewer_keywords:
- C2004
ms.assetid: d81526dd-3a00-4593-87b0-d910d3d29bca
ms.openlocfilehash: b781e9f81342f35d66eca222bd338252b739096c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74737494"
---
# <a name="compiler-error-c2004"></a>Błąd kompilatora C2004

Oczekiwano instrukcji "defined (ID)"

Identyfikator musi występować w nawiasach po słowie kluczowym preprocesora.

Ten błąd może być również wygenerowany w wyniku działania kompilatora, który został wykonany dla programu Visual Studio .NET 2003: brak nawiasu w dyrektywie preprocesora. Jeśli brakuje nawiasu zamykającego w dyrektywie preprocesora, kompilator wygeneruje błąd.

## <a name="example"></a>Przykład

Poniższy przykład generuje C2004:

```cpp
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

```cpp
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
