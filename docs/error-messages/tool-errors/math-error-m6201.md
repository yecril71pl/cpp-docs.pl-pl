---
title: Błąd matematyczny M6201
ms.date: 11/04/2016
f1_keywords:
- M6201
helpviewer_keywords:
- M6201
ms.assetid: 4041c331-d9aa-4dd4-b565-7dbe0218538c
ms.openlocfilehash: 6d3f107de7e45653374036ecafaa864cb3eff5b0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393249"
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