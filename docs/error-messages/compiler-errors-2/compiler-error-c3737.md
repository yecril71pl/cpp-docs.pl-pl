---
title: Błąd kompilatora C3737
ms.date: 11/04/2016
f1_keywords:
- C3737
helpviewer_keywords:
- C3737
ms.assetid: ca2aeb23-2491-4ccb-8838-884abf7065c8
ms.openlocfilehash: b6c2a85556e96ff6176e158b7d75a844bb5710d6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50458633"
---
# <a name="compiler-error-c3737"></a>Błąd kompilatora C3737

"delegowanie": Delegat może nie mieć jawnej konwencji wywoływania

Nie można określić [konwencji wywoływania](../../cpp/calling-conventions.md) dla `delegate`.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3737:

```
// C3737a.cpp
// compile with: /clr
delegate void __stdcall MyFunc();   // C3737
// Try the following line instead.
// delegate void MyFunc();

int main() {
}
```
