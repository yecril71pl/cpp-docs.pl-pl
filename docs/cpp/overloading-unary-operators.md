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
ms.openlocfilehash: 60444ee3c55df39e6b7820ff9b9d7ad81017b0da
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188496"
---
# <a name="overloading-unary-operators"></a>Przeładowanie operatorów jednoargumentowych

Operatory jednoargumentowe, które mogą być przeciążone, są następujące:

1. `!` ([logiczna nie](../cpp/logical-negation-operator-exclpt.md))

1. `&` ([adres](../cpp/address-of-operator-amp.md))

1. `~` ([uzupełnienie jednego](../cpp/one-s-complement-operator-tilde.md))

1. `*` ([dereferencja wskaźnika](../cpp/indirection-operator-star.md))

1. `+` ([jednoargumentowy Plus](../cpp/additive-operators-plus-and.md))

1. `-` ([Negacja Jednoargumentowa](../cpp/additive-operators-plus-and.md))

1. `++` ([Zwiększ](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md))

1. `--` ([zmniejszanie](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md))

9. operatory konwersji

Operatory przyrostu i zmniejszania przyrostkowego (`++` i `--`) są traktowane oddzielnie [i zmniejszają](../cpp/increment-and-decrement-operator-overloading-cpp.md)się.

Operatory konwersji są również omówione w osobnym temacie. Zobacz [konwersje typów zdefiniowane przez użytkownika](../cpp/user-defined-type-conversions-cpp.md).

Następujące reguły są prawdziwe dla wszystkich innych operatorów jednoargumentowych. Aby zadeklarować funkcję operatora jednoargumentowego jako niestatyczny element członkowski, należy zadeklarować ją w postaci:

> *RET-Type —* **operator** *operacja* operatora **()**

gdzie *RET-Type* jest typem zwracanym, a *op* to jeden z operatorów wymienionych w powyższej tabeli.

Aby zadeklarować funkcję operatora jednoargumentowego jako funkcję globalną, należy zadeklarować ją w postaci:

> *RET-Type —* **operator** *operacja* **operatora (** *ARG* **)**

gdzie *RET-Type* i *op* są zgodnie z opisem dla funkcji operatora składowych, a *argument* jest argumentem typu klasy, na którym ma działać.

> [!NOTE]
>  Nie ma żadnych ograniczeń pod względem typów zwracanych operatorów jednoargumentowych. Na przykład ma sensie, że logiczne NOT (`!`) zwraca wartość całkowitą, ale nie jest wymuszane.

## <a name="see-also"></a>Zobacz też

[Przeładowanie operatora](../cpp/operator-overloading.md)
