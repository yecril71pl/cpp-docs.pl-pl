---
title: raw_property_prefixes — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- raw_property_prefixes
dev_langs:
- C++
helpviewer_keywords:
- raw_property_prefixes attribute
ms.assetid: 03a0f48c-c460-4175-a762-9f7f8d84b12f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 423a66b698f4e421ff29e6ac3dfddd11fa11c58f
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/10/2018
ms.locfileid: "42464730"
---
# <a name="rawpropertyprefixes"></a>raw_property_prefixes
**Określonego język C++**  
  
Określa alternatywne prefiksów trzy metody właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```  
raw_property_prefixes("GetPrefix","PutPrefix","PutRefPrefix")  
```  
  
### <a name="parameters"></a>Parametry  
*GetPrefix*  
Prefiks używany dla `propget` metody.  
  
*PutPrefix*  
Prefiks używany dla `propput` metody.  
  
*PutRefPrefix*  
Prefiks używany dla `propputref` metody.  
  
## <a name="remarks"></a>Uwagi  
 
Domyślnie niskiego poziomu `propget`, `propput`, i `propputref` metody są udostępniane przez funkcje składowe o nazwie z prefiksami **rzeczoznawcy**, **put_**, i **putref_** odpowiednio. Te prefiksy są zgodne z nazwami używany w plikach nagłówkowych wygenerowano przez MIDL.  
  
**KONIEC określonego języka C++**  
  
## <a name="see-also"></a>Zobacz też  
 
[atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)   
[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)