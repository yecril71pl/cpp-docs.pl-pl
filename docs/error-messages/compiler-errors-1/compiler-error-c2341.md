---
title: Błąd kompilatora C2341
ms.date: 11/04/2016
f1_keywords:
- C2341
helpviewer_keywords:
- C2341
ms.assetid: aa2a7da5-e1c8-4225-9939-5bdc50158f31
ms.openlocfilehash: 4356182758398fa7ed1ec6a069affa4bb99ace1a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188223"
---
# <a name="compiler-error-c2341"></a>Błąd kompilatora C2341

'Nazwa sekcji': segment musi być zdefiniowany przy użyciu #pragma data_seg, code_seg lub wcześniejszej sekcji, aby użyć

[Przydzielić](../../cpp/allocate.md) odwołuje się do segmentu nie zostały jeszcze zdefiniowane przez [code_seg](../../preprocessor/code-seg.md), [data_seg](../../preprocessor/data-seg.md), lub [sekcji](../../preprocessor/section.md) pragmy.

Poniższy przykład spowoduje wygenerowanie C2341:

```
// C2341.cpp
// compile with: /c
__declspec(allocate(".test"))   // C2341
int j = 1;
```

Możliwe rozwiązanie:

```
// C2341b.cpp
// compile with: /c
#pragma data_seg(".test")
__declspec(allocate(".test"))
int j = 1;
```