---
title: no_smart_pointers — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- no_search_pointers
dev_langs:
- C++
helpviewer_keywords:
- no_smart_pointers attribute
ms.assetid: d69dd71e-08a8-4446-a3d0-a062dc29cb17
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 345da5de492c33107effffb9c97b2fe60906e899
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/10/2018
ms.locfileid: "42466226"
---
# <a name="nosmartpointers"></a>no_smart_pointers
**Określonego język C++**  
  
Pomija Tworzenie inteligentnych wskaźników dla wszystkich interfejsów w bibliotece typów.  
  
## <a name="syntax"></a>Składnia  
  
```  
no_smart_pointers  
```  
  
## <a name="remarks"></a>Uwagi  
 
Domyślnie, gdy używasz `#import`, Pobierz deklarację inteligentny wskaźnik dla wszystkich interfejsów w bibliotece typów. Te inteligentne wskaźniki są typu [_com_ptr_t — klasa](../cpp/com-ptr-t-class.md).  
  
**KONIEC określonego języka C++**  
  
## <a name="see-also"></a>Zobacz też  
 
[atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)   
[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)