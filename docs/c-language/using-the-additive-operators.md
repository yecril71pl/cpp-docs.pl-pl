---
title: Używanie dodatkowych operatorów
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], addition
- additive operators
ms.assetid: 7d54841e-436d-4ae8-9865-1ac1829e6f22
ms.openlocfilehash: 0e2d802a77c56b8f458b614b29e86e2e1d30a55e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62344879"
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

Wartość `i` jest mnożona przez długość wartości **zmiennoprzecinkowej** i dodana do `&x[4]`. Wartość wskaźnika będącego wynikiem jest adres `x[8]`.

```
j = &x[i] - &x[i-2];
```

W tym przykładzie `x` adres trzeciego elementu (określony przez `x[i-2]`) jest odejmowany od adresu piątego elementu `x` (podaną przez `x[i]`). Różnica jest dzielona przez długość **zmiennoprzecinkową**; wynik jest wartością całkowitą 2.

## <a name="see-also"></a>Zobacz też

[Operatory dodawania języka C](../c-language/c-additive-operators.md)
