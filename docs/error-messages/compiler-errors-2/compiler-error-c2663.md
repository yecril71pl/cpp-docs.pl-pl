---
title: Błąd kompilatora C2663 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2663
dev_langs:
- C++
helpviewer_keywords:
- C2663
ms.assetid: 1e93e368-fd52-42bf-9908-9b6df467c8c9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fed35dcce056eb3d2a660c154e94b8058563dba7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46083694"
---
# <a name="compiler-error-c2663"></a>Błąd kompilatora C2663

'Funkcja': liczba przeciążenia mają prawne konwersji dla wskaźnika "this"

Kompilator nie może przekonwertować `this` do dowolnego przeciążone wersje funkcji elementu członkowskiego.

Ten błąd może być spowodowany przez wywołanie innej niż`const` funkcja elementu członkowskiego na `const` obiektu.  Możliwe rozwiązania:

1. Usuń `const` z deklaracja obiektu.

1. Dodaj `const` do jednego z przeciążeń funkcji elementu członkowskiego.

Poniższy przykład spowoduje wygenerowanie C2663:

```
// C2663.cpp
struct C {
   void f() volatile {}
   void f() {}
};

struct D {
   void f() volatile;
   void f() const {}
};

const C *pcc;
const D *pcd;

int main() {
   pcc->f();    // C2663
   pcd->f();    // OK
}
```