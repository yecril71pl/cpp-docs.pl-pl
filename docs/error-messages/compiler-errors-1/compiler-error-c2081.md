---
title: Błąd kompilatora C2081
ms.date: 11/04/2016
f1_keywords:
- C2081
helpviewer_keywords:
- C2081
ms.assetid: 7db9892d-364d-4178-a49d-f8398ece09a0
ms.openlocfilehash: 2e8e813d8162b9a191b6760366b52783e7c8609f
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301993"
---
# <a name="compiler-error-c2081"></a>Błąd kompilatora C2081

"Identyfikator": nazwa w formalnej liście parametrów jest niedozwolona

Identyfikator spowodował błąd składniowy.

Ten błąd może być spowodowany użyciem starego stylu dla formalnej listy parametrów. Należy określić typ parametrów formalnych na liście parametrów formalnych.

Poniższy przykład generuje C2081:

```c
// C2081.c
void func( int i, j ) {}  // C2081, no type specified for j
```

Możliwe rozwiązanie:

```c
// C2081b.c
// compile with: /c
void func( int i, int j ) {}
```
