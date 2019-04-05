---
title: Błąd kompilatora C2674
ms.date: 11/04/2016
f1_keywords:
- C2674
helpviewer_keywords:
- C2674
ms.assetid: 7cbd70d8-d992-44d7-a5cb-dd8cf9c759d2
ms.openlocfilehash: f29371f2987eaae1aa7a56c9f4eb56c332fdf31c
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "58779641"
---
# <a name="compiler-error-c2674"></a>Błąd kompilatora C2674

w tym kontekście deklaracji ogólnej jest niedozwolone.

Element ogólny został zadeklarowany niepoprawnie. Aby uzyskać więcej informacji, zobacz [ogólne](../../extensions/generics-cpp-component-extensions.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C2674.

```
// C2674.cpp
// compile with: /clr /c
void F(generic <class T> ref class R1);   // C2674
generic <class T> ref class R2 {};   // OK
```