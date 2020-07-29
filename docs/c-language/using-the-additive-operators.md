---
title: Używanie dodatkowych operatorów
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], addition
- additive operators
ms.assetid: 7d54841e-436d-4ae8-9865-1ac1829e6f22
ms.openlocfilehash: 06d71f3ad1944976a8d415be9487cb5ea365fa26
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213687"
---
# <a name="using-the-additive-operators"></a>Używanie dodatkowych operatorów

Poniższe przykłady, które ilustrują operatory dodawania i odejmowania, wykorzystują następujące deklaracje:

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

Wartość `i` jest mnożona przez długość **`float`** i dodana do `&x[4]` . Wartość wskaźnika będącego wynikiem jest adres `x[8]` .

```
j = &x[i] - &x[i-2];
```

W tym przykładzie adres trzeciego elementu `x` (określony przez `x[i-2]` ) jest odejmowany od adresu piątego elementu `x` (podaną przez `x[i]` ). Różnica jest dzielona przez długość a **`float`** ; wynik jest wartością całkowitą 2.

## <a name="see-also"></a>Zobacz także

[Operatory addytywne języka C](../c-language/c-additive-operators.md)
