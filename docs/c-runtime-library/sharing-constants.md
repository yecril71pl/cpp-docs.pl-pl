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
ms.workload: cplusplus
ms.openlocfilehash: 635c6eee50f5d1dfb19f0c1b823dab018922c490
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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