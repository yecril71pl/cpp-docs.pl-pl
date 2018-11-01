---
title: Błąd matematyczny M6201
ms.date: 11/04/2016
f1_keywords:
- M6201
helpviewer_keywords:
- M6201
ms.assetid: 4041c331-d9aa-4dd4-b565-7dbe0218538c
ms.openlocfilehash: 6d3f107de7e45653374036ecafaa864cb3eff5b0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50622108"
---
# <a name="math-error-m6201"></a>Błąd matematyczny M6201

'Funkcja': błąd _domeny

Argument do danej funkcji była spoza domeny prawne wartości wejściowe dla tej funkcji.

## <a name="example"></a>Przykład

```
result = sqrt(-1.0)   // C statement
result = SQRT(-1.0)   !  FORTRAN statement
```

Ten błąd wywołania `_matherr` funkcję z nazwy funkcji, argumentów i typ błędu. Można napisać ponownie `_matherr` funkcję, aby dostosować obsługi niektórych błędów zmiennoprzecinkowym zapisu matematycznego w czasie wykonywania.