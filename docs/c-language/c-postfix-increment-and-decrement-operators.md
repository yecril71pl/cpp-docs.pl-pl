---
title: Operatory przyrostka inkrementacji i dekrementacji języka C
ms.date: 11/04/2016
helpviewer_keywords:
- increment operators, syntax
- scalar operators
- types [C], scalar
ms.assetid: 56ba218d-65f9-405f-8684-caccc0ca33aa
ms.openlocfilehash: 8c2e3ba50ce3e768b377a588cd3e82ad29df79ee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325578"
---
# <a name="c-postfix-increment-and-decrement-operators"></a>Operatory przyrostka inkrementacji i dekrementacji języka C

Zwiększ operandy przyrostkowa i operatory dekrementacji są typami skalarnymi, które są modyfikowane przez l wartościami.

## <a name="syntax"></a>Składnia

*postfix-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażeniem przyrostkowym*  **++**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażeniem przyrostkowym*  **--**

Wynik przyrostka inkrementacji i dekrementacji operacji jest wartość operandu. Po uzyskaniu wyniku wartość operandu jest zwiększone (lub zmniejszone). Poniższy kod ilustruje przyrostkowego operatora inkrementacyjnego.

```
if( var++ > 0 )
    *p++ = *q++;
```

W tym przykładzie zmienna `var` jest w porównaniu do 0, a następnie zwiększany. Jeśli `var` dodatnią przed jest zwiększany, następna instrukcja jest wykonywana. Po pierwsze, wartość obiektu wskazywanego przez `q` jest przypisany do obiektu wskazywanego przez `p`. Następnie `q` i `p` są zwiększane.

## <a name="see-also"></a>Zobacz także

[Operatory przyrostka inkrementacji i dekrementacji: ++ i --](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)
