---
title: Kompilator ostrzeżenie (poziom 1) C4114
ms.date: 11/04/2016
f1_keywords:
- C4114
helpviewer_keywords:
- C4114
ms.assetid: 3983e1c6-e8bb-46dc-8894-e1827db48797
ms.openlocfilehash: 41e951e7c4a8b23ddbec14c5421f66702e70c937
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50450976"
---
# <a name="compiler-warning-level-1-c4114"></a>Kompilator ostrzeżenie (poziom 1) C4114

tym samym kwalifikator typu użyty więcej niż raz

Typ deklaracji lub definicji używa kwalifikator typu (**const**, **volatile**, **podpisany**, lub **niepodpisane**) więcej niż jeden raz. Powoduje to ostrzeżenie z rozszerzeniami firmy Microsoft (/Ze) i błąd w ramach zgodności z ANSI (/Za).

Poniższy przykład spowoduje wygenerowanie C4114:

```
// C4114.cpp
// compile with: /W1 /c
volatile volatile int i;   // C4114
```

Poniższy przykład spowoduje wygenerowanie C4114:

```
// C4114_b.cpp
// compile with: /W1 /c
static const int const * ii;   // C4114
static const int * const iii;   // OK
```
