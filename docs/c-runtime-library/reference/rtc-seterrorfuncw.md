---
title: _RTC_SetErrorFuncW
ms.date: 11/04/2016
api_name:
- _RTC_SetErrorFuncW
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _RTC_SetErrorFuncW
- RTC_SetErrorFuncW
helpviewer_keywords:
- run-time errors
- RTC_SetErrorFuncW function
- _RTC_error_fnW typedef
- _RTC_SetErrorFuncW function
- RTC_error_fnW typedef
ms.assetid: b3e0d71f-1bd3-4c37-9ede-2f638eb3c81a
ms.openlocfilehash: 0d45e5c857e917ca23b62482c64a06314565226e
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948965"
---
# <a name="_rtc_seterrorfuncw"></a>_RTC_SetErrorFuncW

Określa funkcję jako program obsługi raportowania błędów czasu wykonywania (RTCs).

## <a name="syntax"></a>Składnia

```C
_RTC_error_fnW _RTC_SetErrorFuncW(
   _RTC_error_fnW function
);
```

### <a name="parameters"></a>Parametry

*funkcyjn*<br/>
Adres funkcji, która będzie obsługiwać sprawdzanie błędów w czasie wykonywania.

## <a name="return-value"></a>Wartość zwracana

Wcześniej zdefiniowana funkcja błędu; lub **wartość null** , jeśli nie ma wcześniej zdefiniowanej funkcji.

## <a name="remarks"></a>Uwagi

W nowym kodzie Używaj tylko **_RTC_SetErrorFuncW**. **_RTC_SetErrorFunc** znajduje się tylko w bibliotece w celu zapewnienia zgodności z poprzednimi wersjami.

Wywołanie zwrotne **_RTC_SetErrorFuncW** ma zastosowanie tylko do składnika, w którym został on połączony, ale nie globalnie.

Upewnij się, że adres przekazany do **_RTC_SetErrorFuncW** ma prawidłową funkcję obsługi błędów.

Jeśli do błędu przypisano typ-1 za pomocą [_RTC_SetErrorType](rtc-seterrortype.md), funkcja obsługi błędów nie jest wywoływana.

Aby można było wywołać tę funkcję, należy najpierw wywołać jedną z funkcji inicjowania sprawdzania błędów w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [Używanie testów w czasie wykonywania bez biblioteki uruchomieniowej C](/visualstudio/debugger/using-run-time-checks-without-the-c-run-time-library).

**_RTC_error_fnW** jest zdefiniowany w następujący sposób:

```cpp
typedef int (__cdecl * _RTC_error_fnW)(
    int errorType,
    const wchar_t * filename,
    int linenumber,
    const wchar_t * moduleName,
    const wchar_t * format,
    ... );
```

gdzie:

*błądtype*<br/>
Typ błędu, który jest określony przez [_RTC_SetErrorType](rtc-seterrortype.md).

*Nazwa pliku*<br/>
Plik źródłowy, w którym wystąpił błąd lub wartość null, jeśli nie ma dostępnych informacji o debugowaniu.

*LineNumber*<br/>
Wiersz w *nazwie pliku* , w którym wystąpił błąd, lub 0, jeśli informacje debugowania nie są dostępne.

*moduleName*<br/>
Nazwa pliku DLL lub pliku wykonywalnego, w którym wystąpił błąd.

*format*<br/>
printf ciąg stylu, aby wyświetlić komunikat o błędzie przy użyciu pozostałych parametrów. Pierwszym argumentem VA_ARGLIST jest numer błędu RTC, który wystąpił.

Aby zapoznać się z przykładem, który pokazuje, jak korzystać z **_RTC_error_fnW**, zobacz [natywne sprawdzanie w czasie wykonywania](/visualstudio/debugger/native-run-time-checks-customization).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_RTC_SetErrorFuncW**|\<rtcapi.h>|

Aby uzyskać więcej informacji, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek uruchomieniowych języka C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Zobacz także

[_CrtDbgReport, _CrtDbgReportW](crtdbgreport-crtdbgreportw.md)<br/>
[Sprawdzanie błędów czasu wykonywania](../../c-runtime-library/run-time-error-checking.md)<br/>
