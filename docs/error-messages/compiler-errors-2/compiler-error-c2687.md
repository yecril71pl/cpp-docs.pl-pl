---
title: C2687 błąd kompilatora
ms.date: 11/04/2016
f1_keywords:
- C2687
helpviewer_keywords:
- C2687
ms.assetid: 1d24b24a-cd0f-41cc-975c-b08dcfb7f402
ms.openlocfilehash: a30efa264a4e7be387c3c2363940bd5ceca1bcc4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50540949"
---
# <a name="compiler-error-c2687"></a>C2687 błąd kompilatora

"type": zgłoszenie wyjątku nie może być "void" lub oznaczeniem typu niekompletnego lub wskaźnikiem bądź odwołaniem do niekompletnego typu

Dla typu jako część deklaracji wyjątku musi być zdefiniowane i nie void.

Poniższy przykład spowoduje wygenerowanie C2687:

```
// C2687.cpp
class C;

int main() {
   try {}
   catch (C) {}   // C2687 error
}
```

Możliwe rozwiązanie:

```
// C2687b.cpp
// compile with: /EHsc
class C {};

int main() {
   try {}
   catch (C) {}
}
```