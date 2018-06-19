---
title: C operatory przyrostka inkrementacji i dekrementacji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- increment operators, syntax
- scalar operators
- types [C], scalar
ms.assetid: 56ba218d-65f9-405f-8684-caccc0ca33aa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8f96c48a69f692c8646de5dec8ad8e6431fb63c5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32381525"
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