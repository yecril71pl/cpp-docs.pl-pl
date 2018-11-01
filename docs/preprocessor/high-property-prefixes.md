---
title: high_property_prefixes
ms.date: 10/18/2018
f1_keywords:
- high_property_prefixes
helpviewer_keywords:
- high_property_prefixes attribute
ms.assetid: 91c6cc2b-19b6-4aba-8831-d9e5cccb58b5
ms.openlocfilehash: 130d19f275612e153955ae49f299fe2f36d098bb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50579819"
---
# <a name="highpropertyprefixes"></a>high_property_prefixes

**Określonego język C++**

Określa alternatywne prefiksów trzy metody właściwości.

## <a name="syntax"></a>Składnia

```
high_property_prefixes("GetPrefix","PutPrefix","PutRefPrefix")
```

### <a name="parameters"></a>Parametry

*GetPrefix*<br/>
Prefiks używany dla `propget` metody.

*PutPrefix*<br/>
Prefiks używany dla `propput` metody.

*PutRefPrefix*<br/>
Prefiks używany dla `propputref` metody.

## <a name="remarks"></a>Uwagi

Domyślnie wysokiego poziomu obsługi błędów `propget`, `propput`, i `propputref` metody są udostępniane przez funkcje składowe o nazwie z prefiksami `Get`, `Put`, i `PutRef`, odpowiednio.

**KONIEC określonego języka C++**

## <a name="see-also"></a>Zobacz też

[atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)