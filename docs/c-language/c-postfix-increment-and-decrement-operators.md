---
title: C operatory przyrostka inkrementacji i dekrementacji | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- increment operators, syntax
- scalar operators
- types [C], scalar
ms.assetid: 56ba218d-65f9-405f-8684-caccc0ca33aa
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9fd1efe80cf5227c682a3bac47299a0daea49e1a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="c-postfix-increment-and-decrement-operators"></a>Operatory przyrostka inkrementacji i dekrementacji języka C
Zwiększ operandy przyrostek i dekrementacji są typy skalarne, które są modyfikowalną l wartości.  
  
## <a name="syntax"></a>Składnia  
 *Operatory przyrostka wyrażenie*:  
 *Operatory przyrostka wyrażenia*  **++**  
  
 *Operatory przyrostka wyrażenia*  **--**  
  
 Wynik operatory przyrostka inkrementacji lub dekrementacji operacji jest wartość argumentu operacji. Po uzyskaniu wyniku wartość operandu jest zwiększone (lub zmniejszone). Poniższy kod ilustruje operator inkrementacji przyrostek.  
  
```  
if( var++ > 0 )  
    *p++ = *q++;  
```  
  
 W tym przykładzie zmienna `var` jest porównywany 0, a następnie zwiększany. Jeśli `var` dodatnią przed jest zwiększany, następna instrukcja jest wykonywana. Po pierwsze, wartość obiektu wskazywana przez `q` jest przypisany do obiektu wskazywana przez `p`. Następnie `q` i `p` są zwiększane.  
  
## <a name="see-also"></a>Zobacz też  
 [Operatory przyrostka inkrementacji i dekrementacji: ++ i --](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)