---
title: raw_property_prefixes
ms.date: 10/18/2018
f1_keywords:
- raw_property_prefixes
helpviewer_keywords:
- raw_property_prefixes attribute
ms.assetid: 03a0f48c-c460-4175-a762-9f7f8d84b12f
ms.openlocfilehash: 23250b524fdaa2181c8e28229ccec680ffdae715
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59033258"
---
# <a name="rawpropertyprefixes"></a>raw_property_prefixes

**Określonego język C++**

Określa alternatywne prefiksów trzy metody właściwości.

## <a name="syntax"></a>Składnia

```
raw_property_prefixes("GetPrefix","PutPrefix","PutRefPrefix")
```

### <a name="parameters"></a>Parametry

*GetPrefix*<br/>
Prefiks używany dla `propget` metody.

*PutPrefix*<br/>
Prefiks używany dla `propput` metody.

*PutRefPrefix*<br/>
Prefiks używany dla `propputref` metody.

## <a name="remarks"></a>Uwagi

Domyślnie niskiego poziomu `propget`, `propput`, i `propputref` metody są udostępniane przez funkcje składowe o nazwie z prefiksami **rzeczoznawcy**, **put_**, i **putref_** odpowiednio. Te prefiksy są zgodne z nazwami używany w plikach nagłówkowych wygenerowano przez MIDL.

**KONIEC określonego języka C++**

## <a name="see-also"></a>Zobacz także

[atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import Directive](../preprocessor/hash-import-directive-cpp.md)