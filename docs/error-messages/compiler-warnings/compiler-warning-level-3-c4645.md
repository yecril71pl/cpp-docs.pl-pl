---
title: Kompilator ostrzeżenie (poziom 3) C4645
ms.date: 11/04/2016
f1_keywords:
- C4645
helpviewer_keywords:
- C4645
ms.assetid: fd7c1ddf-f0d0-4e10-bab9-ccb4c3476298
ms.openlocfilehash: a3e5c834a3f14b9a125176dcddd5bcc355cf1faa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401647"
---
# <a name="compiler-warning-level-3-c4645"></a>Kompilator ostrzeżenie (poziom 3) C4645

Funkcja zadeklarowana ze __declspec(noreturn) zawiera instrukcję return

A [zwracają](../../cpp/return-statement-in-program-termination-cpp.md) instrukcji został znaleziony w funkcji, która jest oznaczona za pomocą [noreturn](../../cpp/noreturn.md) `__declspec` modyfikator. `return` Instrukcji zostało zignorowane.

Poniższy przykład spowoduje wygenerowanie C4645:

```
// C4645.cpp
// compile with:  /W3
void __declspec(noreturn) func() {
   return;   // C4645, delete this line to resolve
}

int main() {
}
```