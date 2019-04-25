---
title: C2687 błąd kompilatora
ms.date: 11/04/2016
f1_keywords:
- C2687
helpviewer_keywords:
- C2687
ms.assetid: 1d24b24a-cd0f-41cc-975c-b08dcfb7f402
ms.openlocfilehash: a30efa264a4e7be387c3c2363940bd5ceca1bcc4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62266195"
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