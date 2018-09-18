---
title: Wyrażenie Evaluation (C) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- expression evaluation
- expressions [C++], evaluating
ms.assetid: 9493f8cc-64a2-4284-9aaf-26eec11c4f40
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0f97b28067d6257ea14255d3e049adcae99f73ef
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46060944"
---
# <a name="expression-evaluation-c"></a>Szacowanie wyrażeń (C)

Wyrażeniami przypisania, przyrost Jednoelementowy, dekrementacja jednoargumentowe lub wywołanie funkcji może mieć skutki uboczne ich oceny (efekty uboczne). Po osiągnięciu "punktu sekwencji" wszystko, czego poprzedzających punktu sekwencji, w tym wszelkie efekty uboczne, jest gwarantowane poddane ocenie, przed rozpoczęciem oceny sporządzania następującego punktu sekwencji.

"Efekty uboczne" zmian spowodowanych wyniku obliczenia wyrażenia. Efekty uboczne występuje po zmianie wartości zmiennej przez Obliczanie wyrażenia. Wszystkie operacje przypisania mają skutki uboczne. Wywołania funkcji można również mieć skutki uboczne w przypadku zmiany wartości elementu widocznego na zewnątrz, przypisania bezpośredniego lub pośredniego przypisania za pomocą wskaźnika.

## <a name="see-also"></a>Zobacz też

[Operandy i wyrażenia](../c-language/operands-and-expressions.md)