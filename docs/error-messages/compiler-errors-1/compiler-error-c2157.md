---
title: Błąd kompilatora C2157
ms.date: 11/04/2016
f1_keywords:
- C2157
helpviewer_keywords:
- C2157
ms.assetid: babbca24-16dc-4b69-be14-a675029249c1
ms.openlocfilehash: 1338a0f0ceb1a42ed84fe74e4ed9a2d774979075
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50450950"
---
# <a name="compiler-error-c2157"></a>Błąd kompilatora C2157

'Funkcja': musi być zadeklarowana przed użyciem w liście pragma

Nazwa funkcji nie jest zadeklarowana przed odwołuje się na liście funkcji [alloc_text](../../preprocessor/alloc-text.md) pragmy.

Poniższy przykład spowoduje wygenerowanie C2157:

```
// C2157.cpp
// compile with: /c
#pragma alloc_text( "func", func)   // C2157

// OK
extern "C" void func();
#pragma alloc_text( "func", func)
```