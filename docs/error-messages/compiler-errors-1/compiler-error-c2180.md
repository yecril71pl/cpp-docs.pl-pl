---
title: Błąd kompilatora C2180
ms.date: 11/04/2016
f1_keywords:
- C2180
helpviewer_keywords:
- C2180
ms.assetid: ea71b39e-b977-48a7-b7bd-af68ef5e263b
ms.openlocfilehash: 5e9444356e536a8369dbcf62cac3c7538d9da5dd
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301902"
---
# <a name="compiler-error-c2180"></a>Błąd kompilatora C2180

wyrażenie kontrolne ma typ "Type"

Wyrażenie kontrolne w instrukcji `if`, `while`, `for`lub `do` jest rzutowane wyrażenia na `void`. Aby rozwiązać ten problem, zmień wyrażenie kontrolne na takie, które tworzy `bool` lub typ, który można przekonwertować na `bool`.

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
