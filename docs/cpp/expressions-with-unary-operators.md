---
title: Wyrażenia z operatorami jednoargumentowymi
ms.date: 11/04/2016
helpviewer_keywords:
- expressions [C++], unary operators
- unary operators [C++], expressions with
- expressions [C++], operators
ms.assetid: 1217685b-b85d-4b48-9ff4-d90f56a26c1b
ms.openlocfilehash: 26aad64e5b9c7a496c2e6bb131b82740c06abe07
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188977"
---
# <a name="expressions-with-unary-operators"></a>Wyrażenia z operatorami jednoargumentowymi

Operatory jednoargumentowe działają tylko dla jednego operandu w wyrażeniu. Operatory jednoargumentowe są następujące:

- [Operator pośredni (*)](../cpp/indirection-operator-star.md)

- [Operator address-of (&)](../cpp/address-of-operator-amp.md)

- [Jednoargumentowy operator plus (+)](../cpp/unary-plus-and-negation-operators-plus-and.md)

- [Jednoargumentowy operator negacji (-)](../cpp/unary-plus-and-negation-operators-plus-and.md)

- [Operator logiczny negacji (!)](../cpp/logical-negation-operator-exclpt.md)

- [Operator uzupełnienia jednego (~)](../cpp/one-s-complement-operator-tilde.md)

- [Operator przyrostu prefiksu (+ +)](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)

- [Operator zmniejszania prefiksu (--)](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)

- [Operator rzutowania ()](../cpp/cast-operator-parens.md)

- [sizeof — Operator](../cpp/sizeof-operator.md)

- [operator __uuidof](../cpp/uuidof-operator.md)

- [operator __alignof](../cpp/alignof-operator.md)

- [operator new](../cpp/new-operator-cpp.md)

- [Usuń operator](../cpp/delete-operator-cpp.md)

Te operatory mają łączność od prawej do lewej. Wyrażenia jednoargumentowe zwykle obejmują składnię, która poprzedza wyrażenie przyrostkowe lub podstawowe.

Poniżej przedstawiono możliwe formy jednoargumentowych wyrażeń.

- *wyrażenie przyrostkowe*

- `++` *wyrażenie jednoargumentowe*

- `--` *wyrażenie jednoargumentowe*

- wyrażenie *jednoargumentowe operatora* *Cast*

- **sizeof** *— wyrażenie jednoargumentowe*

- *Nazwa typu* `sizeof(` `)`

- *wyrażenie* `decltype(` `)`

- *Alokacja — wyrażenie*

- *Cofanie alokacji — wyrażenie*

Każde *wyrażenie przyrostkowe* jest uznawane za *wyrażenie jednoargumentowe*, a ponieważ każde wyrażenie podstawowe jest traktowane jako *wyrażenie przyrostkowe*, wszystkie wyrażenia podstawowe są traktowane także jako *wyrażenie jednoargumentowe* . Aby uzyskać więcej informacji, zobacz [wyrażenia przyrostkowe](../cpp/postfix-expressions.md) i [wyrażenia podstawowe](../cpp/primary-expressions.md).

*Operator jednoargumentowy* składa się z co najmniej jednego z następujących symboli: `* & + - ! ~`

*Wyrażenie cast* jest wyrażeniem jednoargumentowym z opcjonalnym rzutem, aby zmienić typ. Aby uzyskać więcej informacji, zobacz [operator rzutowania: ()](../cpp/cast-operator-parens.md).

*Wyrażenie* może być dowolnym wyrażeniem. Aby uzyskać więcej informacji, zobacz [Expressions](../cpp/expressions-cpp.md).

*Wyrażenie alokacji* odwołuje się do operatora **New** . Cofnięcie *alokacji wyrażenia* odwołuje się do operatora **delete** . Aby uzyskać więcej informacji, zobacz linki we wcześniejszej części tego tematu.

## <a name="see-also"></a>Zobacz też

[Typy wyrażeń](../cpp/types-of-expressions.md)
