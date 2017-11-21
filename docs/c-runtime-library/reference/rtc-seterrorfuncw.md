---
title: "_Rtc_seterrorfuncw — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _RTC_SetErrorFuncW
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
- _RTC_SetErrorFuncW
- RTC_SetErrorFuncW
dev_langs: C++
helpviewer_keywords:
- run-time errors
- RTC_SetErrorFuncW function
- _RTC_error_fnW typedef
- _RTC_SetErrorFuncW function
- RTC_error_fnW typedef
ms.assetid: b3e0d71f-1bd3-4c37-9ede-2f638eb3c81a
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b3285e266091a902373f0bfd7b70b9c1123c19f3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="rtcseterrorfuncw"></a>_RTC_SetErrorFuncW
Określa funkcję jako program obsługi raportowania sprawdzanie błędów czasu wykonywania (RTCs).  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      _RTC_error_fnW _RTC_SetErrorFuncW(  
   _RTC_error_fnW function   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `function`  
 Adres funkcji, która będzie obsługiwać sprawdzanie błędów czasu wykonywania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Funkcja wcześniej zdefiniowanego błąd; lub `NULL` Jeśli żadna funkcja uprzednio zdefiniowany.  
  
## <a name="remarks"></a>Uwagi  
 Nowy kod, używana będzie tylko `_RTC_SetErrorFuncW`. `_RTC_SetErrorFunc`jest dostępny tylko w bibliotece dla zgodności z poprzednimi wersjami.  
  
 `_RTC_SetErrorFuncW` Wywołania zwrotnego ma zastosowanie tylko do składnika, który został połączony, ale nie globalnie.  
  
 Upewnij się, że adres, który jest przekazywany do `_RTC_SetErrorFuncW` jest to, że prawidłowy błąd funkcji obsługi.  
  
 Jeśli błąd został przypisany typ-1 za pomocą [_rtc_seterrortype —](../../c-runtime-library/reference/rtc-seterrortype.md), nie jest wywoływana funkcja obsługi błędów.  
  
 Przed wywołaniem tej funkcji, należy najpierw wywołać jednej z funkcji inicjowania sprawdzanie błędów czasu wykonywania. Aby uzyskać więcej informacji, zobacz [przy użyciu sprawdza bez C Run-Time biblioteki wykonawczej](/visualstudio/debugger/using-run-time-checks-without-the-c-run-time-library).  
  
 **_RTC_error_fnW** jest zdefiniowane w następujący sposób:  
  
 **int — TypeDef (__cdecl \*_RTC_error_fnW) (int** `errorType` **, const wchar_t \***  *filename* **, int** *numer wiersza* **, const wchar_t \***  `moduleName` **, const wchar_t \***  *format* **, ...);**   
  
 gdzie:  
  
 `errorType`  
 Typ błędu, który jest określony przez [_rtc_seterrortype —](../../c-runtime-library/reference/rtc-seterrortype.md).  
  
 *Nazwa pliku*  
 Plik źródłowy, w którym wystąpił błąd, lub wartość null, jeśli nie są dostępne żadne informacje debugowania.  
  
 *numer wiersza*  
 Wiersz w *filename* którym wystąpił błąd lub 0, jeśli nie są dostępne żadne informacje debugowania.  
  
 `moduleName`  
 Biblioteki DLL lub nazwę pliku wykonywalnego, w którym wystąpił błąd.  
  
 *Format*  
 ciąg styl printf wyświetlany komunikat o błędzie, korzystając z pozostałych parametrów. Pierwszy argument VA_ARGLIST jest kod błędu RTC, który wystąpił.  
  
 Na przykład, który przedstawia sposób użycia **_RTC_error_fnW**, zobacz [dostosowywania sprawdza Run-Time natywnego](/visualstudio/debugger/native-run-time-checks-customization).  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_RTC_SetErrorFuncW`|\<rtcapi.h >|  
  
 Aby uzyskać więcej informacji, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Biblioteki  
 Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="see-also"></a>Zobacz też  
 [_Crtdbgreport —, _crtdbgreportw —](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md)   
 [Sprawdzanie błędów czasu wykonywania](../../c-runtime-library/run-time-error-checking.md)