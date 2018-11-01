---
title: Błąd kompilatora C3452
ms.date: 11/04/2016
f1_keywords:
- C3452
helpviewer_keywords:
- C3452
ms.assetid: e5293dcf-cb70-4133-ae2a-0bb496950ba0
ms.openlocfilehash: 165c031f23f3b317300900970b30414da42e7840
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50622758"
---
# <a name="compiler-error-c3452"></a>Błąd kompilatora C3452

składowa listy argumentów nie jest stałą

Przekazano argument atrybut, który oczekuje stałą wartość, które mogą być obliczane w czasie kompilacji.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3452.

```
// C3452.cpp
// compile with: /c
int i;
[module( name="mod", type=dll, custom={i} ) ];   // C3452
// try the following line instead
// [module( name="mod", type=dll, custom={"a"} ) ];
```