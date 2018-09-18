---
title: Przeładowanie operatorów Jednoargumentowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f737e262d39b99c2c33b7c91bc3d1e234a9f47db
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46018629"
---
# <a name="overloading-unary-operators"></a>Przeładowanie operatorów jednoargumentowych

Operatory jednoargumentowe, które mogą być przeciążone, są następujące:

1. `!` ([logiczne NOT](../cpp/logical-negation-operator-exclpt.md))

1. `&` ([adresu](../cpp/address-of-operator-amp.md))

1. `~` ([uzupełnienie jedynkowe](../cpp/one-s-complement-operator-tilde.md))

1. `*` ([wyłuskanie wskaźnika](../cpp/indirection-operator-star.md))

1. `+` ([plus jednoargumentowy](../cpp/additive-operators-plus-and.md))

1. `-` ([Negacja Jednoargumentowa](../cpp/additive-operators-plus-and.md))

1. `++` ([przyrostu](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md))

1. `--` ([dekrementacji](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md))

9. operatory konwersji

Przyrostka inkrementacji i dekrementacji operatorów (`++` i `--`) są omówione oddzielnie w części [AddRef()](../cpp/increment-and-decrement-operator-overloading-cpp.md).

Operatory konwersji zostały również omówione w osobnym temacie; zobacz [konwersje typów zdefiniowane przez użytkownika](../cpp/user-defined-type-conversions-cpp.md).

Następujące reguły są prawdziwe dla wszystkich innych operatorów jednoargumentowych. Aby zadeklarować funkcję operatora jednoargumentowego jako niestatyczny element członkowski, należy zadeklarować ją w postaci:

> *RET-type* **operator** *op* **)**

gdzie *ret-type* jest typem zwracanym i *op* jest jeden z operatorów wymienionych w powyższej tabeli.

Aby zadeklarować funkcję operatora jednoargumentowego jako funkcję globalną, należy zadeklarować ją w postaci:

> *RET-type* **operator** *op* **(** *arg* **)**

gdzie *ret-type* i *op* są opisane dla funkcji operatora składowej i *arg* jest argumentem typu klasy, na którym będą wykonywane.

> [!NOTE]
>  Nie ma żadnych ograniczeń pod względem typów zwracanych operatorów jednoargumentowych. Na przykład, dobrym pomysłem dla logicznego nie (`!`) do zwrócenia wartości całkowitoliczbowej, ale to nie jest wymuszana.

## <a name="see-also"></a>Zobacz także

[Przeładowanie operatora](../cpp/operator-overloading.md)