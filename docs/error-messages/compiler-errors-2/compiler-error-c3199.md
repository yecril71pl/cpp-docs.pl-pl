---
title: Błąd kompilatora C3199
ms.date: 11/04/2016
f1_keywords:
- C3199
helpviewer_keywords:
- C3199
ms.assetid: e7a478d3-115a-40a3-991b-c7454fd2e28e
ms.openlocfilehash: 2f0ca98dc44a78adde378a0f80078ae30c590e11
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738820"
---
# <a name="compiler-error-c3199"></a>Błąd kompilatora C3199

nieprawidłowe użycie zmiennoprzecinkowych pragm: wyjątki nie są obsługiwane w trybie bez dokładności

[Float_control](../../preprocessor/float-control.md) pragma została użyta do określenia modelu wyjątku zmiennoprzecinkowego w ustawieniu [/FP](../../build/reference/fp-specify-floating-point-behavior.md) innym niż **/FP: precyzyjne**.

Poniższy przykład generuje C3199:

```cpp
// C3199.cpp
// compile with: /fp:fast
#pragma float_control(except, on)   // C3199
```
