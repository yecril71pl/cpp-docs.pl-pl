---
title: strerror, _strerror, _wcserror, __wcserror
ms.date: 11/04/2016
api_name:
- strerror
- _strerror
- _wcserror
- __wcserror
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
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 0b4d70687bc2f428162d035c80d6bc8525a8fb9e
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70958149"
---
# <a name="strerror-_strerror-_wcserror-__wcserror"></a>strerror, _strerror, _wcserror, __wcserror

Pobiera ciąg komunikatu o błędzie systemu (**strerror**, **_wcserror**) lub formatuje ciąg komunikatu o błędzie dostarczony przez użytkownika ( **_strerror**, **__wcserror**). Bardziej bezpieczne wersje tych funkcji są dostępne; Zobacz [strerror_s, _strerror_s, _wcserror_s, \__wcserror_s](strerror-s-strerror-s-wcserror-s-wcserror-s.md).

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
Wiadomość dostarczona przez użytkownika.

## <a name="return-value"></a>Wartość zwracana

Wszystkie te funkcje zwracają wskaźnik do ciągu komunikatu o błędzie. Kolejne wywołania mogą zastąpić ciąg.

## <a name="remarks"></a>Uwagi

Funkcja **strerror** mapuje *errnum* na ciąg komunikatu o błędzie i zwraca wskaźnik do ciągu. Nie **strerror** ani **_strerror** rzeczywiście drukuje komunikat: W tym celu należy wywołać funkcję wyjściową, taką jak [fprintf —](fprintf-fprintf-l-fwprintf-fwprintf-l.md):

```C
if (( _access( "datafile",2 )) == -1 )
   fprintf( stderr, _strerror(NULL) );
```

Jeśli *strErrMsg* jest przenoszona jako **null**, **_strerror** zwraca wskaźnik do ciągu, który zawiera komunikat o błędzie systemu dla ostatniego wywołania biblioteki, które spowodowało wystąpienie błędu. Ciąg komunikatu o błędzie jest zakończony znakiem nowego wiersza ("\n"). Jeśli *strErrMsg* nie jest równa **null**, wówczas **_strerror** zwraca wskaźnik do ciągu, który zawiera (w kolejności) komunikat ciągu, dwukropek, spację, komunikat o błędzie systemu dla ostatniego wywołania biblioteki, które powoduje wystąpienie błędu, i wiersz Opis. Ciąg może zawierać maksymalnie 94 znaków.

Rzeczywisty numer błędu dla **_strerror** jest przechowywany w zmiennej [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Aby wygenerować dokładne wyniki, należy wywołać **_strerror** natychmiast po powrocie procedury biblioteki z błędem. W przeciwnym razie kolejne wywołania **strerror** lub **_strerror** mogą zastąpić wartość **errno** .

**_wcserror** i **__wcserror** są odpowiednio wersjami **strerror** i **_strerror**.

**_strerror**, **_wcserror**i **__wcserror** nie są częścią definicji ANSI; są one rozszerzeniami firmy Microsoft i zalecamy, aby nie używać ich w przypadku, gdy potrzebny jest kod przenośny. W przypadku zgodności ze standardem ANSI zamiast tego należy użyć **strerror** .

Aby uzyskać ciągi błędów, zalecamy **strerror** lub **_wcserror** zamiast zaprzestarzałych makr [_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) i [_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) oraz przestarzałych funkcji wewnętrznych **__sys_errlist** i **__sys_nerr**.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _UNICODE & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcserror**|**strerror**|**strerror**|**_wcserror**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**strerror**|\<string.h>|
|**_strerror**|\<string.h>|
|**_wcserror**, **__wcserror**|\<string.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład dla [pError](perror-wperror.md).

## <a name="see-also"></a>Zobacz także

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[clearerr](clearerr.md)<br/>
[ferror](ferror.md)<br/>
[perror, _wperror](perror-wperror.md)<br/>
