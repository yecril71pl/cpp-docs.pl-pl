---
title: Compiler Error C2849
ms.date: 11/04/2016
f1_keywords:
- C2849
helpviewer_keywords:
- C2849
ms.assetid: e28f6b3e-e0e7-4f92-b006-ebaa81d368e6
ms.openlocfilehash: 4812c836d099e9cbb3849e48046edfdeda24ffc9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62256909"
---
# <a name="compiler-error-c2849"></a>Compiler Error C2849

"destruktor": interfejs nie może mieć destruktora

Visual C++ [interfejsu](../../cpp/interface.md) nie może mieć destruktora.

Poniższy przykład spowoduje wygenerowanie C2849:

```
// C2849.cpp
// compile with: /c
__interface C {
   ~C();   // C2849 destructor not allowed in an interface
};
```