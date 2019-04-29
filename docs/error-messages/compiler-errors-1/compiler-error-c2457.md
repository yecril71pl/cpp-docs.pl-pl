---
title: Błąd kompilatora C2457
ms.date: 11/04/2016
f1_keywords:
- C2457
helpviewer_keywords:
- C2457
ms.assetid: 347e169d-23ad-434f-8836-5b09b53980ff
ms.openlocfilehash: a08ac9f9cfbc332b90ad16c663349ee227427278
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62347106"
---
# <a name="compiler-error-c2457"></a>Błąd kompilatora C2457

> "*— makro*": wstępnie zdefiniowane makro nie może występować poza ciałem funkcji

Podjęto próbę użycia wstępnie zdefiniowane makro, takich jak [ &#95; &#95;funkcja&#95;&#95;](../../preprocessor/predefined-macros.md), w globalnej przestrzeni.

## <a name="example"></a>Przykład

Poniższy przykład generuje C2457 oraz pokazuje poprawne użycie:

```cpp
// C2457.cpp
#include <stdio.h>

__FUNCTION__;   // C2457, cannot be global

int main()
{
    printf_s("\n%s", __FUNCTION__);   // OK
}
```