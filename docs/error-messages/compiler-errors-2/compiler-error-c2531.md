---
title: Błąd kompilatora C2531
ms.date: 11/04/2016
f1_keywords:
- C2531
helpviewer_keywords:
- C2531
ms.assetid: c49afe15-55f8-4dc8-ac01-bf653622a7db
ms.openlocfilehash: 03e055e9830b8168fb19885a04c8d40d24713d23
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50567508"
---
# <a name="compiler-error-c2531"></a>Błąd kompilatora C2531

'Identyfikator': odwołanie do nieco pola jest niedozwolony

Odwołania do pola bitowe nie są dozwolone.

Poniższy przykład spowoduje wygenerowanie C2531:

```
// C2531.cpp
// compile with: /c
class P {
   int &b1 : 10;   // C2531
   int b2 : 10;   // OK
};
```