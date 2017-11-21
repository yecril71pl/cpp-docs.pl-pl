---
title: "_WAIT_CHILD —, _WAIT_GRANDCHILD — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _WAIT_GRANDCHILD
- WAIT_CHILD
- WAIT_GRANDCHILD
- _WAIT_CHILD
dev_langs: C++
helpviewer_keywords:
- WAIT_CHILD constant
- WAIT_GRANDCHILD constant
- _WAIT_CHILD constant
- _WAIT_GRANDCHILD constant
ms.assetid: 7acd96fa-d118-4339-bb00-e5afaf286945
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1e5e3aa48f0184730a7860ea055d9b233b4ac708
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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