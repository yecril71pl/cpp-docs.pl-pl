---
title: "Wyrażenie Evaluation (C) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- expression evaluation
- expressions [C++], evaluating
ms.assetid: 9493f8cc-64a2-4284-9aaf-26eec11c4f40
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 21b78b659b4d4cd8f3bb5db849b3c64a5f66f971
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="expression-evaluation-c"></a>Szacowanie wyrażeń (C)
Wyrażeń zawierających przypisania, przyrost jednoargumentowe, dekrementacja jednoargumentowy lub wywołanie funkcji może mieć skutki uboczne ich oceny (efekty uboczne). Po osiągnięciu "punktu sekwencji" wszystko poprzedzających punktu sekwencji, w tym żadnych efektów ubocznych, jest gwarantowane zostało obliczone przed rozpoczęciem oceny na niczego następującego punktu sekwencji.  
  
 "Efekty uboczne" modyfikacje spowodowane przez ocenę wyrażenia. Efekty uboczne występuje po zmianie wartości zmiennej przez Obliczanie wyrażenia. Wszystkie operacje przypisania mieć skutki uboczne. Wywołania funkcji również może mieć efekty uboczne, ich zmiany wartości elementu widoczne na zewnątrz przypisania bezpośredniego lub pośredniego przypisania za pomocą wskaźnika.  
  
## <a name="see-also"></a>Zobacz też  
 [Operandy i wyrażenia](../c-language/operands-and-expressions.md)