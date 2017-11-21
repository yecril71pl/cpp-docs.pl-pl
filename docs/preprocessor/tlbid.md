---
title: TLBID | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: tlbid
dev_langs: C++
helpviewer_keywords: tlbid attribute
ms.assetid: 54b06785-191b-4e77-a9a5-485f2b4acb09
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 526b374dc198ac54ac005f5e46e213667f338c23
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="tlbid"></a>tlbid
**Określonego języka C++**  
  
 Umożliwia ładowanie biblioteki innego niż biblioteki typu podstawowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
tlbid(number)  
```  
  
#### <a name="parameters"></a>Parametry  
 `number`  
 Liczba bibliotekę typów w `filename`.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli wiele biblioteki typów są wbudowane w jednej biblioteki DLL, jej możliwość ładowania bibliotek innych niż biblioteki typu podstawowego przy użyciu `tlbid`.  
  
 Na przykład:  
  
```  
#import <MyResource.dll> tlbid(2)  
```  
  
 odpowiada to:  
  
```  
LoadTypeLib("MyResource.dll\\2");  
```  
  
 **KOŃCOWY określonego języka C++**  
  
## <a name="see-also"></a>Zobacz też  
 [atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)