---
title: Błąd kompilatora C2879
ms.date: 11/04/2016
f1_keywords:
- C2879
helpviewer_keywords:
- C2879
ms.assetid: ac92b645-2394-49de-8632-43d44e0553ed
ms.openlocfilehash: 9ac8f5e5edb1a6ed7314c5b5d125fcc9bfbe67de
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50677958"
---
# <a name="compiler-error-c2879"></a>Błąd kompilatora C2879

'symbol': tylko do istniejącej przestrzeni nazw można przypisać alternatywną nazwę przez definicję aliasu przestrzeni nazw

Nie można utworzyć [alias przestrzeni nazw](../../cpp/namespaces-cpp.md#namespace_aliases) do symbolu innego niż przestrzeni nazw.

Poniższy przykład spowoduje wygenerowanie C2879:

```
// C2879.cpp
int main() {
   int i;
   namespace A = i;   // C2879 i is not a namespace
}
```