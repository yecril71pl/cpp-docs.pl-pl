---
title: "_get_tzname — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _get_tzname
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
- _get_tzname
- get_tzname
dev_langs: C++
helpviewer_keywords:
- _get_tzname function
- time zones
- get_tzname function
ms.assetid: df0065ff-095f-4237-832c-2fe9ab913875
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3f70e928c3877bf5d660231cbe2646f6cf72575e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="gettzname"></a>_get_tzname
Pobiera reprezentacji ciągu znaków nazwy strefy czasowej lub nazwa strefy (czas standardowy) czasu letniego (DST).  
  
## <a name="syntax"></a>Składnia  
  
```  
errno_t _get_tzname(  
    size_t* pReturnValue,  
    char* timeZoneName,  
    size_t sizeInBytes,  
    int index      
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [out]`pReturnValue`  
 Długość ciągu `timeZoneName` włącznie z terminatorem NULL.  
  
 [out]`timeZoneName`  
 Adres ciąg znaków reprezentację Nazwa strefy czasowej lub nazwa strefy (czas standardowy) czasu letniego (DST), w zależności od `index`.  
  
 [in]`sizeInBytes`  
 Rozmiar `timeZoneName` znaków ciągu w bajtach.  
  
 [in]`index`  
 Indeks jednej nazwy dwie strefy czasowej do pobrania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zero, jeśli to się powiedzie, w przeciwnym razie `errno` wpisz wartość.  
  
 Jeśli dowolny `timeZoneName` jest `NULL`, lub `sizeInBytes` jest zerowy lub mniejsza od zera (ale nie oba), program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może kontynuować, ta funkcja ustawia `errno` do `EINVAL` i zwraca `EINVAL`.  
  
### <a name="error-conditions"></a>Warunki błędów  
  
|`pReturnValue`|`timeZoneName`|`sizeInBytes`|`index`|Wartość zwracana|Zawartość`timeZoneName`|  
|--------------------|--------------------|-------------------|-------------|------------------|--------------------------------|  
|rozmiar TZ nazwy|`NULL`|0|0 lub 1|0|Nie zmodyfikowano|  
|rozmiar TZ nazwy|wszystkie|> 0|0 lub 1|0|Nazwa TZ|  
|Nie zmodyfikowano|`NULL`|> 0|wszystkie|`EINVAL`|Nie zmodyfikowano|  
|Nie zmodyfikowano|wszystkie|zero|wszystkie|`EINVAL`|Nie zmodyfikowano|  
|Nie zmodyfikowano|wszystkie|> 0|> 1|`EINVAL`|Nie zmodyfikowano|  
  
## <a name="remarks"></a>Uwagi  
 `_get_tzname` Funkcja pobiera reprezentacja ciągu znaków nazwy strefy czasowej lub nazwa strefy (czas standardowy) czasu letniego (DST) na adres `timeZoneName` w zależności od wartości indeksu oraz rozmiar ciągu w `pReturnValue`. Jeśli `timeZoneName` jest `NULL` i `sizeInBytes` jest zero, po prostu rozmiar ciągu albo czasu strefy w bajtach jest zwracany w `pReturnValue`. Wartości indeksu musi być 0 dla strefy (czas standardowy) lub 1 dla letniej strefy czasowej standard; mają inne wartości indeksu nieokreślonej wyników.  
  
### <a name="index-values"></a>Wartości indeksu  
  
|`index`|Zawartość`timeZoneName`|`timeZoneName`Wartość domyślna|  
|-------------|--------------------------------|----------------------------------|  
|0|Nazwa strefy czasowej|"PST"|  
|1|Nazwa strefy czasu letniego (czas standardowy)|"PDT"|  
|> 1 lub < 0|`errno`wartość`EINVAL`|Nie zmodyfikowano|  
  
 Jeśli wartości są zmieniane jawnie w czasie wykonywania, wartości domyślne to "PST" i "PDT" odpowiednio.  Rozmiary te tablice znaków są regulowane przez `TZNAME_MAX` wartość.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_get_tzname`|\<Time.h >|  
  
 Aby uzyskać więcej informacji, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie czasem](../../c-runtime-library/time-management.md)   
 [errno, _doserrno — _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)   
 [_get_daylight —](../../c-runtime-library/reference/get-daylight.md)   
 [_get_dstbias —](../../c-runtime-library/reference/get-dstbias.md)   
 [_get_timezone —](../../c-runtime-library/reference/get-timezone.md)   
 [TZNAME_MAX](../../c-runtime-library/tzname-max.md)