---
title: Udostępnianie stałych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- _SH_DENYNO
- _SH_DENYRD
- _SH_DENYRW
- _SH_DENYWR
- _SH_COMPAT
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 41060a9dbd3d2bc8176a2b13233db54933a6428b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
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