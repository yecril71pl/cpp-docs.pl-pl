---
title: Ostrzeżenie kompilatora (poziom 3) C4287
ms.date: 11/04/2016
f1_keywords:
- C4287
helpviewer_keywords:
- C4287
ms.assetid: 1bf3bff8-6402-4d06-95ba-431678a790a7
ms.openlocfilehash: 9ea192dddf570d0b41b6531181f4a2fbf51664c2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198916"
---
# <a name="compiler-warning-level-3-c4287"></a>Ostrzeżenie kompilatora (poziom 3) C4287

"operator": niezgodność stałej ze znakiem/bez znaku

Zmienna bez znaku została użyta w operacji z liczbą ujemną.

To ostrzeżenie jest domyślnie wyłączone. Aby uzyskać więcej informacji [, zobacz ostrzeżenia kompilatora, które są domyślnie wyłączone](../../preprocessor/compiler-warnings-that-are-off-by-default.md) .

## <a name="example"></a>Przykład

Poniższy przykład generuje C4287:

```cpp
// C4287.cpp
// compile with: /W3
#pragma warning(default : 4287)
#include <stdio.h>

int main()
{
    unsigned int u = 1;
    if (u < -1)   // C4287
        printf_s("u LT -1");
    else
        printf_s("u !LT -1");
    return 0;
}
```
