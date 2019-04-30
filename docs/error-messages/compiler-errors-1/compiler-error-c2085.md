---
title: Błąd kompilatora C2085
ms.date: 11/04/2016
f1_keywords:
- C2085
helpviewer_keywords:
- C2085
ms.assetid: 0a86785c-8e6f-481b-8c7b-412220c1950d
ms.openlocfilehash: a65e3c0ea622950b99b9ba83fc168b4718d13e46
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345706"
---
# <a name="compiler-error-c2085"></a>Błąd kompilatora C2085

'Identyfikator': nie znajduje się na liście parametrów formalnych

Identyfikator został zadeklarowany w definicji funkcji, ale nie na liście parametrów formalnych. (Tylko ANSI C)

Poniższy przykład spowoduje wygenerowanie C2085:

```
// C2085.c
void func1( void )
int main( void ) {}   // C2085
```

Możliwe rozwiązanie:

```
// C2085b.c
void func1( void );
int main( void ) {}
```

Z brakującymi średnik `func1()` wygląda jak definicja funkcji nie prototyp, więc `main` jest zdefiniowana w `func1()`, generowanie błędu C2085 dla identyfikatora `main`.