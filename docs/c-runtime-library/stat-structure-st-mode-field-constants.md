---
title: stałe pola_stat struktura st_mode | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- S_IFCHR
- S_IFDIR
- _S_IWRITE
- S_IFMT
- _S_IFDIR
- _S_IREAD
- S_IEXEC
- _S_IEXEC
- _S_IFMT
- S_IWRITE
- S_IFREG
- S_IREAD
- _S_IFCHR
- _S_IFREG
dev_langs:
- C++
helpviewer_keywords:
- S_IFDIR constant
- stat structure
- S_IWRITE constant
- S_IEXEC constant
- _S_IFREG constant
- S_IREAD constant
- stat structure, constants
- _S_IFMT constant
- st_mode field constants
- S_IFMT constant
- _S_IEXEC constant
- _S_IWRITE constant
- _S_IFDIR constant
- S_IFREG constant
- S_IFCHR constant
- _S_IREAD constant
- _S_IFCHR constant
ms.assetid: fd462004-7563-4766-8443-30b0a86174b6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f603757706bfdeeaaefe5b6d33cd94bb2624c389
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="stat-structure-stmode-field-constants"></a>Stałe pola_stat Struktura st_mode
## <a name="syntax"></a>Składnia  
  
```  
  
#include <sys/stat.h>  
  
```  
  
## <a name="remarks"></a>Uwagi  
 Stałe te są używane do wskazywania typu pliku w **st_mode** pole [stałe pola_stat struktura](../c-runtime-library/standard-types.md).  
  
 Poniżej opisano stałe maski bitowej:  
  
|Stała|Znaczenie|  
|--------------|-------------|  
|`_S_IFMT`|Maska typu pliku|  
|`_S_IFDIR`|Katalog|  
|`_S_IFCHR`|Znaki specjalne (wskazuje urządzenie, jeśli ustawiona)|  
|`_S_IFREG`|Regularne|  
|`_S_IREAD`|Uprawnienia do odczytu, właściciela|  
|`_S_IWRITE`|Uprawnienia do zapisu właściciela|  
|`_S_IEXEC`|Wykonanie/wyszukiwania uprawnienia właściciela|  
  
## <a name="see-also"></a>Zobacz też  
 [_stat, _wstat — funkcje](../c-runtime-library/reference/stat-functions.md)   
 [_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)   
 [Standardowe typy](../c-runtime-library/standard-types.md)   
 [Stałe globalne](../c-runtime-library/global-constants.md)