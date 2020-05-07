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

Operandy przyrostka przyrostkowego i zmniejszania są typami skalarnymi, które są modyfikowane l-wartości.

## <a name="syntax"></a>Składnia

*wyrażenie przyrostkowe*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie przyrostkowe*  **++**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyrażenie przyrostkowe*  **--**

Wynikiem operacji przyrostka przyrostkowego lub zmniejszania jest wartość operandu. Po uzyskaniu wyniku wartość operandu jest zwiększana (lub zmniejszana). Poniższy kod ilustruje przyrostowy operator przyrostu.

```
if( var++ > 0 )
    *p++ = *q++;
```

W tym przykładzie zmienna `var` jest porównywana z wartością 0, a następnie zwiększana. Jeśli `var` była wynikiem dodatnim przed zwiększeniem wartości, następna instrukcja zostanie wykonana. Najpierw wartość obiektu wskazywanego przez `q` jest przypisana do obiektu wskazywanego przez. `p` Następnie `q` i `p` są zwiększane.

## <a name="see-also"></a>Zobacz też

[Operatory przyrostka inkrementacji i dekrementacji: ++ i --](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)
