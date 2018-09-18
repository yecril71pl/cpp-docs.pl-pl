---
title: Kompilator ostrzeżenie (poziom 1) C4155 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4155
dev_langs:
- C++
helpviewer_keywords:
- C4155
ms.assetid: ba233353-09e3-4195-8127-13a27ddd8d70
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dc6620b788a550e26bedca4df0749feaf2f3a9fd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46074750"
---
# <a name="compiler-warning-level-1-c4155"></a>Kompilator ostrzeżenie (poziom 1) C4155

Usunięcie wyrażenia tablicowego bez użycia formularza tablicy "delete"

Formularza tablicy **Usuń** powinien być używany do usunięcia z tablicy. Ostrzeżenie to pojawia się tylko w ramach zgodności z ANSI (/Za).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4155:

```
// C4155.cpp
// compile with: /Za /W1
#include <stdio.h>

int main(void)
{
    int (*array)[ 10 ] = new int[ 5 ] [ 10 ];
    array[0][0] = 8;

    printf_s("%d\n", array[0][0]);

   delete array;   // C4155
    // try the following line instead
    // delete [] array;   // C4155
}
```