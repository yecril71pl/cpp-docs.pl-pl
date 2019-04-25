---
title: Błąd kompilatora C3737
ms.date: 11/04/2016
f1_keywords:
- C3737
helpviewer_keywords:
- C3737
ms.assetid: ca2aeb23-2491-4ccb-8838-884abf7065c8
ms.openlocfilehash: b6c2a85556e96ff6176e158b7d75a844bb5710d6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62327889"
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
