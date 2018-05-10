---
title: TLBID | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- tlbid
dev_langs:
- C++
helpviewer_keywords:
- tlbid attribute
ms.assetid: 54b06785-191b-4e77-a9a5-485f2b4acb09
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9d651546733f42b1a714ac7a39992fa2d392c8fa
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
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