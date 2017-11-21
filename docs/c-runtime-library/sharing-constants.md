---
title: "Udostępnianie stałych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _SH_DENYNO
- _SH_DENYRD
- _SH_DENYRW
- _SH_DENYWR
- _SH_COMPAT
dev_langs: C++
helpviewer_keywords:
- _SH_DENYRW constant
- SH_DENYRD constant
- _SH_COMPAT constant
- _SH_DENYRD constant
- SH_DENYRW constant
- sharing constants
- SH_DENYNO constant
- _SH_DENYWR constant
- SH_DENYWR constant
- _SH_DENYNO constant
- SH_COMPAT constant
ms.assetid: 95fadc3a-55dc-473d-98b5-e8211900465d
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 941cf63dd7a5eb761881e7068fa141d5e6b87a33
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="sharing-constants"></a>Udostępnianie stałych
Stałe dla udostępniania plików trybów.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
#include <share.h>  
  
```  
  
## <a name="remarks"></a>Uwagi  
 *Shflag* argument określa tryb współdzielenia, która składa się z co najmniej jedną stałą manifestu. Może być łączone z *oflag* argumentów (zobacz [plik — stałe](../c-runtime-library/file-constants.md)).  
  
 W poniższej tabeli wymieniono stałe i ich znaczenie:  
  
|Stała|Znaczenie|  
|--------------|-------------|  
|`_SH_DENYRW`|Nie zezwala na odczyt i zapis do pliku|  
|`_SH_DENYWR`|Nie zezwala na dostęp do zapisu do pliku|  
|`_SH_DENYRD`|Nie zezwala na dostęp do odczytu do plików|  
|`_SH_DENYNO`|Zezwoleń do odczytu i zapisu|  
|`_SH_SECURE`|Ustawia tryb bezpieczny (odczyt udostępnionego, wyłączny dostęp do zapisu).|  
  
## <a name="see-also"></a>Zobacz też  
 [_sopen —, _wsopen —](../c-runtime-library/reference/sopen-wsopen.md)   
 [_fsopen —, _wfsopen —](../c-runtime-library/reference/fsopen-wfsopen.md)   
 [Stałe globalne](../c-runtime-library/global-constants.md)