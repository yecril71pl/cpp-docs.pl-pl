---
title: C przyrostka inkrementacji i dekrementacji | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 57fe65f83cff8e4a469270100eb68ec1f29cbb1e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46110266"
---
# <a name="c-postfix-increment-and-decrement-operators"></a>Operatory przyrostka inkrementacji i dekrementacji języka C

Zwiększ operandy przyrostkowa i operatory dekrementacji są typami skalarnymi, które są modyfikowane przez l wartościami.

## <a name="syntax"></a>Składnia

*wyrażeniem przyrostkowym*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażeniem przyrostkowym*  **++**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażeniem przyrostkowym*  **--**

Wynik przyrostka inkrementacji i dekrementacji operacji jest wartość operandu. Po uzyskaniu wyniku wartość operandu jest zwiększone (lub zmniejszone). Poniższy kod ilustruje przyrostkowego operatora inkrementacyjnego.

```
if( var++ > 0 )
    *p++ = *q++;
```

W tym przykładzie zmienna `var` jest w porównaniu do 0, a następnie zwiększany. Jeśli `var` dodatnią przed jest zwiększany, następna instrukcja jest wykonywana. Po pierwsze, wartość obiektu wskazywanego przez `q` jest przypisany do obiektu wskazywanego przez `p`. Następnie `q` i `p` są zwiększane.

## <a name="see-also"></a>Zobacz też

[Operatory przyrostka inkrementacji i dekrementacji: ++ i --](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)