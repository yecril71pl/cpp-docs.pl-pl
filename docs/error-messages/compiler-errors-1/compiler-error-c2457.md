---
title: C2457 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2457
dev_langs:
- C++
helpviewer_keywords:
- C2457
ms.assetid: 347e169d-23ad-434f-8836-5b09b53980ff
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 61cdb4f4b679bab858717a6fb96838f389822a6b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33224926"
---
# <a name="compiler-error-c2457"></a>C2457 błąd kompilatora

> "*makro*": wstępnie zdefiniowane makro nie może występować poza ciałem funkcji

Podjęto próbę użycia wstępnie zdefiniowanego makra, takich jak [ &#95; &#95;funkcja&#95;&#95;](../../preprocessor/predefined-macros.md), w globalnej przestrzeni.

## <a name="example"></a>Przykład

Poniższy przykład generuje C2457 i przedstawiono również poprawne użycie:

```cpp
// C2457.cpp
#include <stdio.h>

__FUNCTION__;   // C2457, cannot be global

int main()
{
    printf_s("\n%s", __FUNCTION__);   // OK
}
```