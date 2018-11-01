---
title: Błąd kompilatora C2541
ms.date: 11/04/2016
f1_keywords:
- C2541
helpviewer_keywords:
- C2541
ms.assetid: ed95180f-00df-4e62-a8e9-1b6dab8281bf
ms.openlocfilehash: d8b2366bc2899b7a2ac76b0fae133351cd88a541
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50564557"
---
# <a name="compiler-error-c2541"></a>Błąd kompilatora C2541

"delete": Usuń: nie można usunąć obiektów, które nie są wskaźnikami

[Usuń](../../cpp/delete-operator-cpp.md) operator została użyta na obiekt, który nie jest wskaźnikiem.

Poniższy przykład spowoduje wygenerowanie C2541:

```
// C2541.cpp
int main() {
   int i;
   delete i;   // C2541 i not a pointer

   // OK
   int *ip = new int;
   delete ip;
}
```