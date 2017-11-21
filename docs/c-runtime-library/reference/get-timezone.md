---
title: "_get_timezone — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _get_timezone
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-time-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _get_timezone
- get_timezone
dev_langs: C++
helpviewer_keywords:
- time zones
- get_timezone function
- _get_timezone function
ms.assetid: 30ab0838-0ae9-4a2f-bfe6-a49ee443b21e
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 46181817aaf455ef777ba479a1bd2abe774ba792
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="gettimezone"></a>_get_timezone
Pobiera różnica w sekundach między uniwersalny czas koordynowany (UTC) i czasem lokalnym.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      error_t _get_timezone(   
    long* seconds  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `seconds`  
 Różnica w sekundach między czasem UTC i czasem lokalnym.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zera w razie powodzenia lub `errno` wartość, gdy wystąpi błąd.  
  
## <a name="remarks"></a>Uwagi  
 `_get_timezone` Funkcja pobiera różnica w sekundach między czasem UTC a lokalnym jako liczba całkowita. Wartością domyślną jest 28 800 sekund dla pacyficznego czasu standardowego (osiem godzin za UTC).  
  
 Jeśli `seconds` jest `NULL`, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może kontynuować, ta funkcja ustawia `errno` do `EINVAL` i zwraca `EINVAL`.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_get_timezone`|\<Time.h >|  
  
 Aby uzyskać więcej informacji, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie czasem](../../c-runtime-library/time-management.md)   
 [errno, _doserrno — _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)   
 [_get_daylight —](../../c-runtime-library/reference/get-daylight.md)   
 [_get_dstbias —](../../c-runtime-library/reference/get-dstbias.md)   
 [_get_tzname —](../../c-runtime-library/reference/get-tzname.md)