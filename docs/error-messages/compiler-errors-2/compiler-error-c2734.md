---
title: Błąd kompilatora C2734
ms.date: 11/04/2016
f1_keywords:
- C2734
helpviewer_keywords:
- C2734
ms.assetid: e53a77b7-825c-42d1-a655-90e1c93b833e
ms.openlocfilehash: a188948a6d7ea7902b2df548819ffb8c40486dbc
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755775"
---
# <a name="compiler-error-c2734"></a>Błąd kompilatora C2734

"Identyfikator": obiekt const musi zostać zainicjowany, jeśli nie jest zewnętrzny

Identyfikator jest zadeklarowany `const` ale nie został zainicjowany lub `extern`.

Poniższy przykład generuje C2734:

```cpp
// C2734.cpp
const int j;   // C2734
extern const int i;   // OK, declared as extern
```
