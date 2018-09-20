---
title: high_property_prefixes — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 6f188cd833551542e636e764e76784635ae2ccf2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46422769"
---
# <a name="highpropertyprefixes"></a>high_property_prefixes
**Określonego język C++**  
  
Określa alternatywne prefiksów trzy metody właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```  
high_property_prefixes("GetPrefix","PutPrefix","PutRefPrefix")  
```  
  
### <a name="parameters"></a>Parametry  
*GetPrefix*  
Prefiks używany dla `propget` metody.  
  
*PutPrefix*  
Prefiks używany dla `propput` metody.  
  
*PutRefPrefix*  
Prefiks używany dla `propputref` metody.  
  
## <a name="remarks"></a>Uwagi  
 
Domyślnie wysokiego poziomu obsługi błędów `propget`, `propput`, i `propputref` metody są udostępniane przez funkcje składowe o nazwie z prefiksami `Get`, `Put`, i `PutRef`, odpowiednio.  
  
**KONIEC określonego języka C++**  
  
## <a name="see-also"></a>Zobacz też  
 
[atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)