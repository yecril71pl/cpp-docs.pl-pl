---
title: Błąd kompilatora C2180
ms.date: 11/04/2016
f1_keywords:
- C2180
helpviewer_keywords:
- C2180
ms.assetid: ea71b39e-b977-48a7-b7bd-af68ef5e263b
ms.openlocfilehash: 3794a1ce0fcbe60c06cb3efca45a3081e85c17ce
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87210023"
---
# <a name="compiler-error-c2180"></a>Błąd kompilatora C2180

wyrażenie kontrolne ma typ "Type"

Wyrażenie kontrolne w **`if`** instrukcji, **`while`** , **`for`** lub **`do`** jest rzutowane na wyrażenie **`void`** . Aby rozwiązać ten problem, zmień wyrażenie kontrolne na takie, które tworzy **`bool`** lub typ, który można przekonwertować na **`bool`** .

Poniższy przykład generuje C2180:

```c
// C2180.c

int main() {
   while ((void)1)   // C2180
      return 1;
   while (1)         // OK
      return 0;
}
```
