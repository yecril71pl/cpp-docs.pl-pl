---
title: strerror, _strerror, _wcserror, __wcserror
ms.date: 11/04/2016
apiname:
- strerror
- _strerror
- _wcserror
- __wcserror
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- __sys_errlist
- wcserror
- _strerror
- __wcserror
- strerror
- __sys_nerr
- _tcserror
- _wcserror
- tcserror
helpviewer_keywords:
- strerror function
- _strerror function
- __sys_errlist
- wcserror function
- error messages, printing
- __sys_nerr
- tcserror function
- printing error messages
- _wcserror function
- _tcserror function
- __wcserror function
- error messages, getting
ms.assetid: 27b72255-f627-43c0-8836-bcda8b003e14
ms.openlocfilehash: 4038fcc29c18e5d73024cbe5688c674e00d1409e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594652"
---
# <a name="strerror-strerror-wcserror-wcserror"></a>strerror, _strerror, _wcserror, __wcserror

Pobiera ciąg komunikatu o błędzie systemu (**strerror**, **_wcserror —**) ani nie formatuje ciąg komunikatu o błędzie dostarczony przez użytkownika (**_strerror —**, **__wcserror —**). Bardziej bezpieczne wersje tych funkcji są dostępne; zobacz [strerror_s —, _strerror_s —, _wcserror_s —, \__wcserror_s —](strerror-s-strerror-s-wcserror-s-wcserror-s.md).

## <a name="syntax"></a>Składnia

```C
char *strerror(
   int errnum
);
char *_strerror(
   const char *strErrMsg
);
wchar_t * _wcserror(
   int errnum
);
wchar_t * __wcserror(
   const wchar_t *strErrMsg
);
```

### <a name="parameters"></a>Parametry

*errnum*<br/>
Numer błędu.

*strErrMsg*<br/>
Wiadomości dostarczone przez użytkownika.

## <a name="return-value"></a>Wartość zwracana

Wszystkie te funkcje zwracają wskaźnik do ciągu komunikat o błędzie. Kolejne wywołania może spowodować zastąpienie ciągu.

## <a name="remarks"></a>Uwagi

**Strerror** funkcja mapy *errnum* komunikat o błędzie ciąg i zwraca wskaźnik do ciągu. Ani **strerror** ani **_strerror —** faktycznie drukują komunikatu: W tym należy wywołać funkcję danych wyjściowych, takich jak [fprintf](fprintf-fprintf-l-fwprintf-fwprintf-l.md):

```C
if (( _access( "datafile",2 )) == -1 )
   fprintf( stderr, _strerror(NULL) );
```

Jeśli *strErrMsg* jest przekazywany jako **NULL**, **_strerror —** zwraca wskaźnik do ciągu, który zawiera komunikat o błędzie systemu dla ostatniego wywołania biblioteki, które powoduje błąd. Ciąg komunikatu o błędzie jest zakończony przez znak nowego wiersza (\n). Jeśli *strErrMsg* nie jest równa **NULL**, następnie **_strerror —** zwraca wskaźnik do ciągu, który zawiera (w kolejności) komunikat ciągu, dwukropek, spację, błąd systemu komunikat dla ostatniego wywołania biblioteki, które generuje błąd i znak nowego wiersza. Ciąg wiadomości może być co najwyżej 94 znaki długości.

Numer błędu dla **_strerror —** jest przechowywana w zmiennej [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Aby wygenerować dokładne wyniki, należy wywołać **_strerror —** natychmiast, po procedurze biblioteki zwraca błąd. W przeciwnym razie, kolejne wywołania **strerror** lub **_strerror —** może spowodować zastąpienie **errno** wartości.

**_wcserror —** i **__wcserror —** są wersjami znaków dwubajtowych **strerror** i **_strerror —**, odpowiednio.

**_strerror —**, **_wcserror —**, i **__wcserror —** nie są częścią definicji ANSI; są rozszerzenia Microsoft i firma Microsoft zaleca, aby używać ich, w której chcesz przenośny kod. Dla zgodności ANSI, użyj **strerror** zamiast tego.

Aby uzyskać ciągi błędów, zaleca się **strerror** lub **_wcserror —** zamiast przestarzałych makra [_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) i [_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) i przestarzałe funkcje wewnętrzne **__sys_errlist** i **__sys_nerr**.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcserror —**|**strerror**|**strerror**|**_wcserror**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**strerror**|\<string.h>|
|**_strerror**|\<string.h>|
|**_wcserror —**, **__wcserror —**|\<string.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [perror](perror-wperror.md).

## <a name="see-also"></a>Zobacz także

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[clearerr](clearerr.md)<br/>
[ferror](ferror.md)<br/>
[perror, _wperror](perror-wperror.md)<br/>
