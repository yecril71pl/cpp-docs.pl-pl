---
title: Błąd kompilatora C2231
ms.date: 11/04/2016
f1_keywords:
- C2231
helpviewer_keywords:
- C2231
ms.assetid: 677c5c66-d30f-4c3b-bbb9-760858d56477
ms.openlocfilehash: 50230b3a9b609d281cddf996783287c270f844d5
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301824"
---
# <a name="compiler-error-c2231"></a>Błąd kompilatora C2231

".": Lewy argument operacji wskazuje na "Class-Key", użyj "->"

Operand po lewej stronie operacji wyboru elementu członkowskiego (.) jest wskaźnikiem, a nie klasą, strukturą lub Unią.

Poniższy przykład generuje C2231:

```c
// C2231.c
struct S {
   int member;
} s, *ps = &s;
int main() {
   ps.member = 0;   // C2231

   // OK
   ps->member = 0;   // crash
   s.member = 0;
}
```
