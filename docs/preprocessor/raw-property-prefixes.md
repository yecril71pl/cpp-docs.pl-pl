---
title: "raw_property_prefixes — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: raw_property_prefixes
dev_langs: C++
helpviewer_keywords: raw_property_prefixes attribute
ms.assetid: 03a0f48c-c460-4175-a762-9f7f8d84b12f
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: aec8daa33e5fc734168bcb3096c4111536250c68
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="rawpropertyprefixes"></a>raw_property_prefixes
**Określonego języka C++**  
  
 Określa alternatywny prefiksów dla trzech metod właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```  
raw_property_prefixes("GetPrefix","PutPrefix","PutRefPrefix")  
```  
  
#### <a name="parameters"></a>Parametry  
 `GetPrefix`  
 Prefiks do zastosowania w przypadku **propget** metody.  
  
 `PutPrefix`  
 Prefiks do zastosowania w przypadku **propput** metody.  
  
 `PutRefPrefix`  
 Prefiks do zastosowania w przypadku **propputref** metody.  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie niskiego poziomu **propget**, **propput**, i **propputref** metody są udostępniane przez funkcje elementu członkowskiego o nazwie z prefiksami **get_**, **put_**, i **putref_** odpowiednio. Tymi prefiksami są zgodne z nazwami używany w plikach nagłówka wygenerowano przez MIDL.  
  
 **KOŃCOWY określonego języka C++**  
  
## <a name="see-also"></a>Zobacz też  
 [atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)