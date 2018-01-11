---
title: "high_property_prefixes — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: high_property_prefixes
dev_langs: C++
helpviewer_keywords: high_property_prefixes attribute
ms.assetid: 91c6cc2b-19b6-4aba-8831-d9e5cccb58b5
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ed37cdc51c5e08899786ce82a9c3e5e3224f9f9e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="highpropertyprefixes"></a>high_property_prefixes
**Określonego języka C++**  
  
 Określa alternatywny prefiksów dla trzech metod właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```  
high_property_prefixes("GetPrefix","PutPrefix","PutRefPrefix")  
```  
  
#### <a name="parameters"></a>Parametry  
 `GetPrefix`  
 Prefiks do zastosowania w przypadku **propget** metody.  
  
 `PutPrefix`  
 Prefiks do zastosowania w przypadku **propput** metody.  
  
 `PutRefPrefix`  
 Prefiks do zastosowania w przypadku **propputref** metody.  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie wysokiego poziomu obsługi błędów **propget**, **propput**, i **propputref** metody są udostępniane przez funkcje elementu członkowskiego o nazwie z prefiksami **Get** , `Put`, i **PutRef**odpowiednio.  
  
 **KOŃCOWY określonego języka C++**  
  
## <a name="see-also"></a>Zobacz też  
 [atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)