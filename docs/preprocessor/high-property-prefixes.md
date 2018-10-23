---
title: high_property_prefixes — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- high_property_prefixes
dev_langs:
- C++
helpviewer_keywords:
- high_property_prefixes attribute
ms.assetid: 91c6cc2b-19b6-4aba-8831-d9e5cccb58b5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e3932a7632b12120e722c5f375f4387e08f1853b
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/23/2018
ms.locfileid: "49809060"
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