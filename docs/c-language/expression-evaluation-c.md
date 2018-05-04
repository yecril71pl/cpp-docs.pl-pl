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
ms.openlocfilehash: 9c250cba9e26d82ba129a842b61006783d13f6e3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="expression-evaluation-c"></a>Szacowanie wyrażeń (C)
Wyrażeń zawierających przypisania, przyrost jednoargumentowe, dekrementacja jednoargumentowy lub wywołanie funkcji może mieć skutki uboczne ich oceny (efekty uboczne). Po osiągnięciu "punktu sekwencji" wszystko poprzedzających punktu sekwencji, w tym żadnych efektów ubocznych, jest gwarantowane zostało obliczone przed rozpoczęciem oceny na niczego następującego punktu sekwencji.  
  
 "Efekty uboczne" modyfikacje spowodowane przez ocenę wyrażenia. Efekty uboczne występuje po zmianie wartości zmiennej przez Obliczanie wyrażenia. Wszystkie operacje przypisania mieć skutki uboczne. Wywołania funkcji również może mieć efekty uboczne, ich zmiany wartości elementu widoczne na zewnątrz przypisania bezpośredniego lub pośredniego przypisania za pomocą wskaźnika.  
  
## <a name="see-also"></a>Zobacz też  
 [Operandy i wyrażenia](../c-language/operands-and-expressions.md)