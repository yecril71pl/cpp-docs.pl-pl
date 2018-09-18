---
title: 'Operatory jednoargumentowe Plus i negacji: + i - | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- +
- '-'
dev_langs:
- C++
helpviewer_keywords:
- unary operators [C++], plus
- '- operator'
- negation operator
- + operator [C++], unary operators
- + operator
ms.assetid: 2c58c4f4-0d92-4ae3-9d0c-1a6157875cc1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0ef8cc91f90f92d17ec759c874c7dfd34b4706e9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032877"
---
# <a name="unary-plus-and-negation-operators--and--"></a>Operatory jednoargumentowe plus i negacji: + i -

## <a name="syntax"></a>Składnia

```
+ cast-expression
- cast-expression
```

## <a name="-operator"></a>+ — Operator

Wynik Jednoargumentowy operator plus (**+**) to wartość swojego operandu. Argument operacji do Jednoargumentowy operator plus musi być typu arytmetycznego.

Promocja typu całkowitego odbywa się w przypadku argumentów operacji typu całkowitego. Wynikowy typ to typ, do którego argument jest podnoszony. W związku z tym, wyrażenie `+ch`, gdzie `ch` typu **char**, typ **int**; wartość pozostaje niezmieniona. Zobacz [konwersje standardowe](standard-conversions.md) uzyskać więcej informacji o jak jest wykonywane podwyższenia poziomu.

## <a name="--operator"></a>- — Operator

Jednoargumentowy operator negacji (**-**) daje wartość negatywną swojego operandu. Argument operacji do Jednoargumentowy operator negacji musi być typu arytmetycznego.

Promocja typu całkowitego odbywa się w przypadku argumentów operacji typu całkowitego, a wynikowy typ jest typem, do którego argument jest podnoszony. Zobacz [konwersje standardowe](standard-conversions.md) Aby uzyskać więcej informacji na temat sposobu promowania jest wykonywane.

## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft

Negacja Jednoargumentowa o ilości nieznaczonych odbywa się przez odjęcie wartości argumentu z 2 ^ n, gdzie n to liczba bitów w obiekcie o danym typie bez znaku.

## <a name="see-also"></a>Zobacz także

[Wyrażenia z operatorami jednoargumentowymi](../cpp/expressions-with-unary-operators.md)<br/>
[Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)