---
title: Błąd kompilatora C2227 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2227
dev_langs:
- C++
helpviewer_keywords:
- C2227
ms.assetid: d470e8b8-7e15-468b-84fa-37d1a0132271
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f446cc09ab8799714141aefb45fa4aefc8b940e7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46078455"
---
# <a name="compiler-error-c2227"></a>Błąd kompilatora C2227

po lewej "-> elementu członkowskiego" musi wskazywać typ klasy/struct/union/generic

Argument operacji po lewej stronie `->` nie jest wskaźnik do klasy, struktury lub Unii.

Poniższy przykład spowoduje wygenerowanie C2227:

```
// C2227.cpp
int *pInt;
struct S {
public:
    int member;
} s, *pS = &s;

int main() {
   pInt->member = 0;   // C2227 pInt points to an int
   pS->member = 0;   // OK
}
```