---
title: Błąd kompilatora C2457
ms.date: 11/04/2016
f1_keywords:
- C2457
helpviewer_keywords:
- C2457
ms.assetid: 347e169d-23ad-434f-8836-5b09b53980ff
ms.openlocfilehash: 40e666b1f2b566ca6309ee7759452647f8101a38
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205247"
---
# <a name="compiler-error-c2457"></a>Błąd kompilatora C2457

> "*makro*": wstępnie zdefiniowane makro nie może występować poza treścią funkcji

Podjęto próbę użycia wstępnie zdefiniowanego makra, takiego [ &#95; &#95;jak&#95;funkcja](../../preprocessor/predefined-macros.md), w obszarze globalnym.

## <a name="example"></a>Przykład

Poniższy przykład generuje C2457, a także wyświetla poprawne użycie:

```cpp
// C2457.cpp
#include <stdio.h>

__FUNCTION__;   // C2457, cannot be global

int main()
{
    printf_s("\n%s", __FUNCTION__);   // OK
}
```
