---
title: high_property_prefixes
ms.date: 10/18/2018
f1_keywords:
- high_property_prefixes
helpviewer_keywords:
- high_property_prefixes attribute
ms.assetid: 91c6cc2b-19b6-4aba-8831-d9e5cccb58b5
ms.openlocfilehash: 3f8975ec9737e02bb1216166cc6c241549e95a07
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59029372"
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

## <a name="see-also"></a>Zobacz także

[atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import Directive](../preprocessor/hash-import-directive-cpp.md)