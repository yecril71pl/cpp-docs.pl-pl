---
title: "C2457 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2457
dev_langs: C++
helpviewer_keywords: C2457
ms.assetid: 347e169d-23ad-434f-8836-5b09b53980ff
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ff89bb3635936ae0f797438d73f71adf1ef08de7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2457"></a>C2457 błąd kompilatora

> "*makro*": wstępnie zdefiniowane makro nie może występować poza ciałem funkcji

Podjęto próbę użycia wstępnie zdefiniowanego makra, takich jak [&#95; &#95; Funkcja &#95; &#95; ](../../preprocessor/predefined-macros.md), w globalnej przestrzeni.

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