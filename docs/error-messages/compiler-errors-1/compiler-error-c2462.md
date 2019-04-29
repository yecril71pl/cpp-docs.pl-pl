---
title: Błąd kompilatora C2462
ms.date: 11/04/2016
f1_keywords:
- C2462
helpviewer_keywords:
- C2462
ms.assetid: a8601bf8-f5ce-41de-9117-e2632bd4996b
ms.openlocfilehash: 0b342f8b878c48a77336fab4921cf4a668e248ab
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62368295"
---
# <a name="compiler-error-c2462"></a>Błąd kompilatora C2462

'Identyfikator': nie można zdefiniować typu w "nowe wyrażenie"

Nie można zdefiniować typu w dziedzinie operand `new` operatora. Definicja typu należy umieścić w osobnych instrukcji.

Poniższy przykład spowoduje wygenerowanie C2462:

```
// C2462.cpp
int main() {
   new struct S { int i; };   // C2462
}
```