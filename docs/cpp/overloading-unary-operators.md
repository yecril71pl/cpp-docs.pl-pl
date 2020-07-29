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
ms.openlocfilehash: a21c62549f02dddda951c79a06617671ccfe2526
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227221"
---
# <a name="overloading-unary-operators"></a>Przeładowanie operatorów jednoargumentowych

Operatory jednoargumentowe, które mogą być przeciążone, są następujące:

1. `!`([logiczne not](../cpp/logical-negation-operator-exclpt.md))

1. `&`([adres-z](../cpp/address-of-operator-amp.md))

1. `~`([uzupełnienie jednego](../cpp/one-s-complement-operator-tilde.md))

1. `*`([odwołuje](../cpp/indirection-operator-star.md)się do wskaźnika)

1. `+`([jednoargumentowy Plus](../cpp/additive-operators-plus-and.md))

1. `-`([Negacja Jednoargumentowa](../cpp/additive-operators-plus-and.md))

1. `++`([Zwiększ](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md))

1. `--`([zmniejszenie](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md))

1. operatory konwersji

Operatory przyrostu i zmniejszania przyrostkowego ( `++` i `--` ) są traktowane osobno przy [zwiększeniu i zmniejszeniu](../cpp/increment-and-decrement-operator-overloading-cpp.md).

Operatory konwersji są również omówione w osobnym temacie. Zobacz [konwersje typów zdefiniowane przez użytkownika](../cpp/user-defined-type-conversions-cpp.md).

Następujące reguły są prawdziwe dla wszystkich innych operatorów jednoargumentowych. Aby zadeklarować funkcję operatora jednoargumentowego jako niestatyczny element członkowski, należy zadeklarować ją w postaci:

> *RET-Type* **`operator`** *op* **()**

gdzie *RET-Type* jest typem zwracanym, a *op* to jeden z operatorów wymienionych w powyższej tabeli.

Aby zadeklarować funkcję operatora jednoargumentowego jako funkcję globalną, należy zadeklarować ją w postaci:

> *RET-Type* **`operator`** *op* **(** *ARG* **)**

gdzie *RET-Type* i *op* są zgodnie z opisem dla funkcji operatora składowych, a *argument* jest argumentem typu klasy, na którym ma działać.

> [!NOTE]
> Nie ma żadnych ograniczeń pod względem typów zwracanych operatorów jednoargumentowych. Załóżmy na przykład, że dla logicznego nie ( `!` ) ma zostać zwrócona wartość całkowita, ale nie jest wymuszana.

## <a name="see-also"></a>Zobacz także

[Przeciążanie operatora](../cpp/operator-overloading.md)
