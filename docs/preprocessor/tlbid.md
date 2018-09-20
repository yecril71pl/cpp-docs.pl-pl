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
ms.openlocfilehash: f5bd922089bcf189c403a97679a593a985603a12
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46446260"
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
 
[atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)