---
title: Błąd kompilatora C2085 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2085
dev_langs:
- C++
helpviewer_keywords:
- C2085
ms.assetid: 0a86785c-8e6f-481b-8c7b-412220c1950d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d88968e49e38a13782dde2d905a614ad4d177e81
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46082381"
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