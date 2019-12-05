---
title: 'Operatory jednoargumentowe plus i negacji: + i -'
ms.date: 11/04/2016
f1_keywords:
- +
- '-'
helpviewer_keywords:
- unary operators [C++], plus
- '- operator'
- negation operator
- + operator [C++], unary operators
- + operator
ms.assetid: 2c58c4f4-0d92-4ae3-9d0c-1a6157875cc1
ms.openlocfilehash: 83fedd9d3cc6cd7c08ba79d2ed83e9f62d919e29
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857245"
---
# <a name="unary-plus-and-negation-operators--and--"></a>Operatory jednoargumentowe plus i negacji: + i -

## <a name="syntax"></a>Składnia

```
+ cast-expression
- cast-expression
```

## <a name="-operator"></a>+ — Operator

Wynik operatora jednoargumentowego plus ( **+** ) jest wartością operandu. Argument operacji operatora jednoargumentowego plus musi być typu arytmetycznego.

Promocja typu całkowitego jest wykonywana w przypadku całkowitych argumentów operacji. Typ wynikowy to typ, do którego zostanie podwyższony operand. W tym celu wyrażenie `+ch`, gdzie `ch` jest typu **char**, daje w wyniku typ **int**; wartość nie jest modyfikowana. Zobacz [standardowe konwersje](standard-conversions.md) , aby uzyskać więcej informacji na temat sposobu przeprowadzania promocji.

## <a name="--operator"></a>- — Operator

Jednoargumentowy operator negacji ( **-** ) zwraca wartość ujemną argumentu operacji. Argument operacji operatora jednoargumentowego negacji musi być typem arytmetycznym.

Promocja całkowa jest wykonywana na całkowitych operandach, a wynikowy typ to typ, do którego zostanie podwyższony operand. Zobacz [standardowe konwersje](standard-conversions.md) , aby uzyskać więcej informacji na temat sposobu przeprowadzania podwyższania poziomu.

**Microsoft Specific**

Jednoargumentowa Negacja nieoznaczonych ilości jest wykonywana przez odjęcie wartości operandu z 2 ^ n, gdzie n to liczba bitów w obiekcie danego niepodpisanego typu.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Wyrażenia z operatorami jednoargumentowymi](../cpp/expressions-with-unary-operators.md)<br/>
[Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)