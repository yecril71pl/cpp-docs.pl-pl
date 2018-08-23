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
ms.openlocfilehash: 1ec0150e63209728cf2f02c854fe03702b8a45b4
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/10/2018
ms.locfileid: "42464828"
---
# <a name="tlbid"></a>tlbid
**Określonego język C++**  
  
Umożliwia ładowanie bibliotek innych niż biblioteki typu podstawowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
tlbid(number)  
```  
  
### <a name="parameters"></a>Parametry  
*Numer*  
Liczba bibliotekę typów w `filename`.  
  
## <a name="remarks"></a>Uwagi  
 
Jeśli wiele bibliotek typów są wbudowane w pojedynczego pliku DLL, możliwe do załadowania biblioteki inne niż biblioteki typu podstawowego, za pomocą **tlbid**.  
  
Na przykład:  
  
```  
#import <MyResource.dll> tlbid(2)  
```  
  
jest równoważne:  
  
```  
LoadTypeLib("MyResource.dll\\2");  
```  
  
**KONIEC określonego języka C++**  
  
## <a name="see-also"></a>Zobacz też  
 
[atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)   
[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)