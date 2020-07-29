---
title: Błąd kompilatora C2464
ms.date: 11/04/2016
f1_keywords:
- C2464
helpviewer_keywords:
- C2464
ms.assetid: ace953d6-b414-49ee-bfef-90578a8da00c
ms.openlocfilehash: b2d2766b11d15bdb666baa207591cc9ff279a280
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225478"
---
# <a name="compiler-error-c2464"></a>Błąd kompilatora C2464

"Identyfikator": nie można użyć "New", aby przydzielić odwołanie

Identyfikator odwołania został przydzielony do **`new`** operatora. Odwołania nie są obiektami pamięci, dlatego **`new`** nie można zwrócić do nich wskaźnika. Użyj składni deklaracji zmiennej standardowej, aby zadeklarować odwołanie.

Poniższy przykład generuje C2464:

```cpp
// C2464.cpp
int main() {
   new ( int& ir );   // C2464
}
```
