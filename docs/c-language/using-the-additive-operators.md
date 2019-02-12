---
title: Używanie dodatkowych operatorów
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], addition
- additive operators
ms.assetid: 7d54841e-436d-4ae8-9865-1ac1829e6f22
ms.openlocfilehash: 0e2d802a77c56b8f458b614b29e86e2e1d30a55e
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56151432"
---
# <a name="using-the-additive-operators"></a>Używanie dodatkowych operatorów

Poniższe przykłady, które ilustrują operatorów dodawania i odejmowania, użyto tych deklaracji:

```
int i = 4, j;
float x[10];
float *px;
```

Te instrukcje są równoważne:

```
px = &x[4 + i];
px = &x[4] + i;
```

Wartość `i` jest mnożony przez długość **float** i dodane do `&x[4]`. Wynikowa wartość wskaźnika jest adresem `x[8]`.

```
j = &x[i] - &x[i-2];
```

W tym przykładzie adres trzeci element `x` (przez `x[i-2]`) jest odejmowany od adres piąty element `x` (przez `x[i]`). Różnica jest podzielona przez długość **float**; wynik jest wartością całkowitą 2.

## <a name="see-also"></a>Zobacz także

[Operatory dodawania języka C](../c-language/c-additive-operators.md)
