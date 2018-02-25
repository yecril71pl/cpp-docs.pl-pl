---
title: TLBID | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- tlbid
dev_langs:
- C++
helpviewer_keywords:
- tlbid attribute
ms.assetid: 54b06785-191b-4e77-a9a5-485f2b4acb09
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 52cb9237537e151e699974fe91c5a7a99725513f
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
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