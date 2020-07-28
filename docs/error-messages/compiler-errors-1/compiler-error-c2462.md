---
title: Błąd kompilatora C2462
ms.date: 11/04/2016
f1_keywords:
- C2462
helpviewer_keywords:
- C2462
ms.assetid: a8601bf8-f5ce-41de-9117-e2632bd4996b
ms.openlocfilehash: 8db79bf9813d9701b45d9a0427f68cfbecc3eba4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214675"
---
# <a name="compiler-error-c2462"></a>Błąd kompilatora C2462

"Identyfikator": nie można zdefiniować typu w "New-Expression"

Nie można zdefiniować typu w polu operand **`new`** operatora. Umieść definicję typu w oddzielnej instrukcji.

Poniższy przykład generuje C2462:

```cpp
// C2462.cpp
int main() {
   new struct S { int i; };   // C2462
}
```
