---
title: Przeładowanie operatorów jednoargumentowych
ms.date: 11/04/2016
helpviewer_keywords:
- unary operators [C++], plus
- increment operators [C++], overloaded
- unary operators [C++], minus
- operators [C++], unary
- redefinable unary operators [C++]
- unary operators [C++]
- pointer dereference operator overloading
- plus operator
ms.assetid: 7683ef08-42a4-4283-928f-d3dd4f3ab4c0
ms.openlocfilehash: 971ef08c5e79f851c502ea872c541517065797c5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372032"
---
# <a name="overloading-unary-operators"></a>Przeładowanie operatorów jednoargumentowych

Operatory jednoargumentowe, które mogą być przeciążone, są następujące:

1. `!`([logiczne NIE](../cpp/logical-negation-operator-exclpt.md))

1. `&`([adres)](../cpp/address-of-operator-amp.md)

1. `~`[(dopełnienie)](../cpp/one-s-complement-operator-tilde.md)

1. `*`[(wyłudnik wskaźnika)](../cpp/indirection-operator-star.md)

1. `+`([bezemisowe plus](../cpp/additive-operators-plus-and.md))

1. `-`([negacja bezparżyszna)](../cpp/additive-operators-plus-and.md)

1. `++`[(przyrost)](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)

1. `--`([dekrementowanie](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md))

1. operatory konwersji

Operatory przyrostu i dekrementacji`++` `--`(i) są traktowane oddzielnie w [increment i Decrement](../cpp/increment-and-decrement-operator-overloading-cpp.md).

Operatory konwersji są również omawiane w osobnym temacie; zobacz [Konwersje typu zdefiniowane przez użytkownika](../cpp/user-defined-type-conversions-cpp.md).

Następujące reguły są prawdziwe dla wszystkich innych operatorów jednoargumentowych. Aby zadeklarować funkcję operatora jednoargumentowego jako niestatyczny element członkowski, należy zadeklarować ją w postaci:

> *operator typu ret* **operator** *op* **()**

gdzie *ret-type* jest typem zwracany i *op* jest jednym z operatorów wymienionych w powyższej tabeli.

Aby zadeklarować funkcję operatora jednoargumentowego jako funkcję globalną, należy zadeklarować ją w postaci:

> *operator typu ret* **operator** *op* **(** *arg* **)**

gdzie *ret typu* i *op* są opisane dla funkcji operatora elementu członkowskiego i *arg* jest argumentem typu klasy, na którym mają działać.

> [!NOTE]
> Nie ma żadnych ograniczeń pod względem typów zwracanych operatorów jednoargumentowych. Na przykład ma sens dla`!`logicznego NIE ( ) do zwrócenia wartości integralnej, ale nie jest to wymuszane.

## <a name="see-also"></a>Zobacz też

[Przeciążenie operatora](../cpp/operator-overloading.md)
