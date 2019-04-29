---
title: _RTC_SetErrorFuncW
ms.date: 11/04/2016
apiname:
- _RTC_SetErrorFuncW
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
helpviewer_keywords:
- run-time errors
- RTC_SetErrorFuncW function
- _RTC_error_fnW typedef
- _RTC_SetErrorFuncW function
- RTC_error_fnW typedef
ms.assetid: b3e0d71f-1bd3-4c37-9ede-2f638eb3c81a
ms.openlocfilehash: 03e9f540a215550a698700f28e5722b33b119149
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62357229"
---
# <a name="rtcseterrorfuncw"></a>_RTC_SetErrorFuncW

Określa funkcję jako program obsługi raportowania sprawdzanie błędów czasu wykonywania (RTCs).

## <a name="syntax"></a>Składnia

```C
_RTC_error_fnW _RTC_SetErrorFuncW(
   _RTC_error_fnW function
);
```

### <a name="parameters"></a>Parametry

*— Funkcja*<br/>
Adres funkcji, która będzie obsługiwać sprawdzanie błędów czasu wykonywania.

## <a name="return-value"></a>Wartość zwracana

Funkcję wcześniej zdefiniowaną błędu; lub **NULL** Jeśli nie ma zdefiniowanej wcześniej funkcji.

## <a name="remarks"></a>Uwagi

W nowym kodzie, używana będzie tylko **_RTC_SetErrorFuncW**. **_RTC_SetErrorFunc** jest dostępny tylko w bibliotece zgodności z poprzednimi wersjami.

**_RTC_SetErrorFuncW** wywołania zwrotnego, który ma zastosowanie tylko do składnika, który był połączony, ale nie globalny.

Upewnij się, że adres, który jest przekazywany do **_RTC_SetErrorFuncW** jest fakt, że prawidłowy funkcji obsługi błędu.

Jeśli błąd został przypisany typ -1 za pomocą [_RTC_SetErrorType](rtc-seterrortype.md), nie zostanie wywołana funkcja obsługi błędów.

Przed wywołaniem tej funkcji, najpierw musisz wywołać jedną z funkcji inicjowania sprawdzanie błędów czasu wykonywania. Aby uzyskać więcej informacji, zobacz [przy użyciu biblioteki czasu wykonywania sprawdza, czy bez C Run-Time](/visualstudio/debugger/using-run-time-checks-without-the-c-run-time-library).

**_RTC_error_fnW** jest zdefiniowana w następujący sposób:

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

*errorType*<br/>
Typ błędu, który jest określony przez [_RTC_SetErrorType](rtc-seterrortype.md).

*Nazwa pliku*<br/>
Plik źródłowy, w którym wystąpił błąd, lub wartość null, jeśli są dostępne żadne informacje debugowania.

*numer wiersza*<br/>
Wiersz w *filename* moment wystąpienia awarii lub 0, jeśli są dostępne żadne informacje debugowania.

*moduleName*<br/>
Plik DLL lub nazwą pliku wykonywalnego, w którym wystąpił błąd.

*Format*<br/>
ciąg stylu printf wyświetlany komunikat o błędzie, za pomocą pozostałych parametrów. Pierwszy argument VA_ARGLIST jest numer błędu RTC, który wystąpił.

Aby uzyskać przykład, w którym pokazano, jak **_RTC_error_fnW**, zobacz [natywnego środowiska wykonawczego sprawdza dostosowywania](/visualstudio/debugger/native-run-time-checks-customization).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_RTC_SetErrorFuncW**|\<rtcapi.h>|

Aby uzyskać więcej informacji, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Zobacz także

[_CrtDbgReport, _CrtDbgReportW](crtdbgreport-crtdbgreportw.md)<br/>
[Sprawdzanie błędów czasu wykonywania](../../c-runtime-library/run-time-error-checking.md)<br/>
