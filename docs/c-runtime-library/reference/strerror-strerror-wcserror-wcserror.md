---
title: strerror —, a _strerror —, _wcserror —, __wcserror — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e89a5de45baeb9b3beea2aa538cb0a2168f3c5ed
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="strerror-strerror-wcserror-wcserror"></a>strerror, _strerror, _wcserror, __wcserror

Pobiera ciąg z komunikatem o system (**strerror —**, **_wcserror —**) lub Formatuje ciąg z komunikatem o dostarczone przez użytkownika (**_strerror —**, **__wcserror —**). Bezpieczniejsza wersje te funkcje są dostępne; zobacz [strerror_s —, _strerror_s —, _wcserror_s —, \__wcserror_s —](strerror-s-strerror-s-wcserror-s-wcserror-s.md).

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
Komunikat dostarczone przez użytkownika.

## <a name="return-value"></a>Wartość zwracana

Wszystkie te funkcje zwraca wskaźnik do ciągu komunikat o błędzie. Kolejne wywołania mogą zastąpić ciąg.

## <a name="remarks"></a>Uwagi

**Strerror —** funkcji mapy *errnum* na ciąg komunikat o błędzie i zwraca wskaźnik do ciągu. Ani **strerror —** ani **_strerror —** faktycznie drukuje wiadomości: W tym masz wywołania funkcji wyjścia, takich jak [fprintf —](fprintf-fprintf-l-fwprintf-fwprintf-l.md):

```C
if (( _access( "datafile",2 )) == -1 )
   fprintf( stderr, _strerror(NULL) );
```

Jeśli *strErrMsg* jest przekazywany jako **NULL**, **_strerror —** zwraca wskaźnik do ciąg, który zawiera komunikat o błędzie systemu ostatniego połączenia biblioteki, który powoduje błąd. Komunikat o błędzie ciąg kończy się znakiem nowego wiersza ("\n"). Jeśli *strErrMsg* nie jest równa **NULL**, następnie **_strerror —** zwraca wskaźnik na ciąg, który zawiera (w kolejności) wiadomości ciąg, dwukropek, spację, błąd systemu komunikat dla ostatniego wywołania biblioteki, które generuje błąd i znaku nowego wiersza. Ciąg komunikatu może zawierać co najwyżej 94 znaków.

Numer błędu **_strerror —** jest przechowywana w zmiennej [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Aby uzyskać dokładne wyniki, należy wywołać **_strerror —** natychmiast po procedury biblioteki zwraca błąd. W przeciwnym razie kolejne wywołania **strerror —** lub **_strerror —** mogą zastąpić **errno** wartości.

**_wcserror —** i **__wcserror —** wersji znaków dwubajtowych **strerror —** i **_strerror —**odpowiednio.

**_strerror —**, **_wcserror —**, i **__wcserror —** nie są częścią definicji ANSI; są one rozszerzenia Microsoft i firma Microsoft zaleca, aby używać ich miejscu kod przenośny. Zgodność ANSI, użyj **strerror —** zamiast tego.

Aby uzyskać ciągów błędów, zaleca się **strerror —** lub **_wcserror —** zamiast przestarzałych makra [_sys_errlist —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) i [_sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) i przestarzałe funkcje wewnętrznej **__sys_errlist** i **__sys_nerr**.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|
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
