---
title: Błąd kompilatora C2528
ms.date: 11/04/2016
f1_keywords:
- C2528
helpviewer_keywords:
- C2528
ms.assetid: 2ea9d583-67a8-4b16-b35f-a50eeffc03c4
ms.openlocfilehash: 890dae7aa34103bde0168f1933bb42343d84100b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50601750"
---
# <a name="compiler-error-c2528"></a>Błąd kompilatora C2528

"name": wskaźnik do odwołania jest niedozwolone

Nie można zadeklarować wskaźnik do odwołania. Dereference zmiennej przed zadeklarowaniem wskaźnika do niego.

Poniższy przykład spowoduje wygenerowanie C2528:

```
// C2528.cpp
int i;
int &ir = i;
int & (*irptr) = ir;    // C2528
```