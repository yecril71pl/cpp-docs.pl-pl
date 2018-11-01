---
title: Błąd kompilatora C3353
ms.date: 11/04/2016
f1_keywords:
- C3353
helpviewer_keywords:
- C3353
ms.assetid: 5699c04b-d504-46ce-bf71-c200318fed71
ms.openlocfilehash: eb7b55f63e911f155c13e777e2e84ae7b587e9a3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50432672"
---
# <a name="compiler-error-c3353"></a>Błąd kompilatora C3353

"delegowanie": delegat można tworzyć tylko z globalnej funkcji lub funkcji składowej typu zarządzanego lub typu WinRT

Delegatów, zadeklarowany za pomocą [delegować](../../windows/delegate-cpp-component-extensions.md) — słowo kluczowe, mogą być deklarowane tylko w zakresie globalnym.

Poniższy przykład spowoduje wygenerowanie C3353:

```
// C3353.cpp
// compile with: /clr
delegate int f;   // C3353
```