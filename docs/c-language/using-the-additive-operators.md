---
title: Używanie dodatkowych operatorów
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], addition
- additive operators
ms.assetid: 7d54841e-436d-4ae8-9865-1ac1829e6f22
ms.openlocfilehash: 78dc559a83626057603027e30742435b1128e31c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50557693"
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

## <a name="see-also"></a>Zobacz też

[Operatory dodawania języka C](../c-language/c-additive-operators.md)