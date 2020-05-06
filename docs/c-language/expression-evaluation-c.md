---
title: Szacowanie wyrażeń (C)
ms.date: 11/04/2016
helpviewer_keywords:
- expression evaluation
- expressions [C++], evaluating
ms.assetid: 9493f8cc-64a2-4284-9aaf-26eec11c4f40
ms.openlocfilehash: 37affedc0bcf3fb1423898ecf2c570794d9625c0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62233850"
---
# <a name="expression-evaluation-c"></a>Szacowanie wyrażeń (C)

Wyrażenia związane z przypisaniem, przyrostem jednoargumentowym, zmniejszeniem jednoargumentowym lub wywołaniem funkcji mogą mieć konsekwencje przypadkowe do oceny (skutki uboczne). Po osiągnięciu "punktu sekwencji" wszystkie elementy poprzedzające punkt sekwencji, w tym wszystkie efekty uboczne, są gwarantowane przed rozpoczęciem oceny, które zaczynają się od punktu sekwencji.

"Skutki uboczne" są zmianami spowodowanymi przez oszacowanie wyrażenia. Efekt uboczny występuje zawsze, gdy wartość zmiennej jest zmieniana przez oszacowanie wyrażenia. Wszystkie operacje przypisania mają efekty uboczne. Wywołania funkcji mogą także mieć skutki uboczne, jeśli zmieniają wartość widocznej zewnętrznie elementu przez przypisanie bezpośrednie lub przez przypisanie pośrednie przez wskaźnik.

## <a name="see-also"></a>Zobacz też

[Operandy i wyrażenia](../c-language/operands-and-expressions.md)
