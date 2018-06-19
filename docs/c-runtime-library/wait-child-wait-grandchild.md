---
title: _WAIT_CHILD —, _WAIT_GRANDCHILD — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- _WAIT_GRANDCHILD
- WAIT_CHILD
- WAIT_GRANDCHILD
- _WAIT_CHILD
dev_langs:
- C++
helpviewer_keywords:
- WAIT_CHILD constant
- WAIT_GRANDCHILD constant
- _WAIT_CHILD constant
- _WAIT_GRANDCHILD constant
ms.assetid: 7acd96fa-d118-4339-bb00-e5afaf286945
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 84e0f195bebd43ced767f05a7c6073a6d6e9db61
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32408028"
---
# <a name="waitchild-waitgrandchild"></a>_WAIT_CHILD, _WAIT_GRANDCHILD
## <a name="syntax"></a>Składnia  
  
```  
  
#include <process.h>  
  
```  
  
## <a name="remarks"></a>Uwagi  
 `_cwait` Funkcja może służyć przez jakikolwiek proces oczekiwania na inny proces (jeśli jest znany identyfikator procesu). Argument akcja może mieć jedną z następujących wartości:  
  
|Stała|Znaczenie|  
|--------------|-------------|  
|`_WAIT_CHILD`|Proces wywołania oczekuje, aż określony nowy proces zakończy się.|  
|`_WAIT_GRANDCHILD`|Wywoływanie czeka proces do określonego nowy proces i wszystkie procesy utworzone przez tego nowego procesu, przerwanie.|  
  
## <a name="see-also"></a>Zobacz też  
 [_cwait —](../c-runtime-library/reference/cwait.md)   
 [Stałe globalne](../c-runtime-library/global-constants.md)