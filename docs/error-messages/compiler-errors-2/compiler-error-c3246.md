---
title: Błąd kompilatora C3246
ms.date: 11/04/2016
f1_keywords:
- C3246
helpviewer_keywords:
- C3246
ms.assetid: ad85224a-e540-479b-a5eb-a3bc3964c30b
ms.openlocfilehash: eb5ba268508922daf00adb49cf611c038db76343
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62173200"
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
