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

Wyrażeniami przypisania, przyrost Jednoelementowy, dekrementacja jednoargumentowe lub wywołanie funkcji może mieć skutki uboczne ich oceny (efekty uboczne). Po osiągnięciu "punktu sekwencji" wszystko, czego poprzedzających punktu sekwencji, w tym wszelkie efekty uboczne, jest gwarantowane poddane ocenie, przed rozpoczęciem oceny sporządzania następującego punktu sekwencji.

"Efekty uboczne" zmian spowodowanych wyniku obliczenia wyrażenia. Efekty uboczne występuje po zmianie wartości zmiennej przez Obliczanie wyrażenia. Wszystkie operacje przypisania mają skutki uboczne. Wywołania funkcji można również mieć skutki uboczne w przypadku zmiany wartości elementu widocznego na zewnątrz, przypisania bezpośredniego lub pośredniego przypisania za pomocą wskaźnika.

## <a name="see-also"></a>Zobacz także

[Operandy i wyrażenia](../c-language/operands-and-expressions.md)
