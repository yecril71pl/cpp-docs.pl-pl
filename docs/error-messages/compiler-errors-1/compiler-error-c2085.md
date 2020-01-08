---
title: Błąd kompilatora C2085
ms.date: 11/04/2016
f1_keywords:
- C2085
helpviewer_keywords:
- C2085
ms.assetid: 0a86785c-8e6f-481b-8c7b-412220c1950d
ms.openlocfilehash: 7dbf7266a6330a1fdb46d7f2df90e7684f026d9a
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301967"
---
# <a name="compiler-error-c2085"></a>Błąd kompilatora C2085

"Identyfikator": nie należy do formalnej listy parametrów

Identyfikator został zadeklarowany w definicji funkcji, ale nie znajduje się na liście parametrów formalnych. (Tylko ANSI C)

Poniższy przykład generuje C2085:

```c
// C2085.c
void func1( void )
int main( void ) {}   // C2085
```

Możliwe rozwiązanie:

```c
// C2085b.c
void func1( void );
int main( void ) {}
```

Gdy brakuje średnika, `func1()` wygląda jak definicja funkcji, a nie prototyp, więc `main` jest zdefiniowany w `func1()`, generując C2085 błędów dla `main`identyfikatora.
