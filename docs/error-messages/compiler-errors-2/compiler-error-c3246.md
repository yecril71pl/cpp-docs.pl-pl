---
title: Błąd kompilatora C3246
ms.date: 11/04/2016
f1_keywords:
- C3246
helpviewer_keywords:
- C3246
ms.assetid: ad85224a-e540-479b-a5eb-a3bc3964c30b
ms.openlocfilehash: eb5ba268508922daf00adb49cf611c038db76343
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "58776704"
---
# <a name="compiler-error-c3246"></a>Błąd kompilatora C3246

"class": nie może dziedziczyć z "type", ponieważ został zadeklarowany jako "sealed"

Klasa, która jest oznaczona jako [zapieczętowanego](../../extensions/sealed-cpp-component-extensions.md) nie może być klasą bazową dla innych klas.

Poniższy przykład spowoduje wygenerowanie C3246:

```
// C3246_2.cpp
// compile with: /clr /LD
ref class X sealed {};

ref class Y : public X {}; // C3246
```
