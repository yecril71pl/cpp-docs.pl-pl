---
title: "_Rtc_seterrorfunc — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _RTC_SetErrorFunc
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
apitype: DLLExport
f1_keywords:
- RTC_SetErrorFunc
- _RTC_SetErrorFunc
dev_langs: C++
helpviewer_keywords:
- RTC_SetErrorFunc function
- _RTC_SetErrorFunc function
ms.assetid: b2292722-0d83-4092-83df-3d5b19880666
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: fa6d2e05668eac7909cb7805c5843ee6584b941f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="rtcseterrorfunc"></a>_RTC_SetErrorFunc
Określa funkcję jako program obsługi raportowania sprawdzanie błędów czasu wykonywania (RTCs). Ta funkcja jest przestarzała; Użyj `_RTC_SetErrorFuncW` zamiast tego.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      _RTC_error_fn _RTC_SetErrorFunc(  
   _RTC_error_fn function   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 *Funkcja*  
 Adres funkcji, która będzie obsługiwać sprawdzanie błędów czasu wykonywania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Funkcja wcześniej zdefiniowanego błędu. Jeśli nie ma żadnej wcześniej określonych funkcji, zwraca wartość NULL.  
  
## <a name="remarks"></a>Uwagi  
 Nie używaj tej funkcji; Zamiast tego należy użyć `_RTC_SetErrorFuncW`. Zachowywane tylko dla zgodności z poprzednimi wersjami.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_RTC_SetErrorFunc`|\<rtcapi.h >|  
  
 Aby uzyskać więcej informacji, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Biblioteki  
 Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="see-also"></a>Zobacz też  
 [_Crtdbgreport —, _crtdbgreportw —](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md)   
 [Sprawdzanie błędów czasu wykonywania](../../c-runtime-library/run-time-error-checking.md)