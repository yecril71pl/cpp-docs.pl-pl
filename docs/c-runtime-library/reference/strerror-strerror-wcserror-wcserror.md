---
title: strerror, _strerror, _wcserror, __wcserror
description: Opisuje funkcje biblioteki środowiska uruchomieniowego Microsoft C (CRT) strerror, _strerror, _wcserror i __wcserror.
ms.date: 01/07/2020
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
ms.openlocfilehash: 8c9c6850d6620407897b2a3a1dbf32e61f6719c0
ms.sourcegitcommit: 7bd3567fc6a0e7124aab51cad63bbdb44a99a848
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75755050"
---
# <a name="strerror-_strerror-_wcserror-__wcserror"></a>strerror, _strerror, _wcserror, __wcserror

Pobiera ciąg komunikatu o błędzie systemu (**strerror**, **_wcserror**) lub formatuje ciąg komunikatu o błędzie dostarczony przez użytkownika ( **_strerror**, **__wcserror**). Bardziej bezpieczne wersje tych funkcji są dostępne; Zobacz [strerror_s, _strerror_s, _wcserror_s \__wcserror_s](strerror-s-strerror-s-wcserror-s-wcserror-s.md).

## <a name="syntax"></a>Składnia

```C
char * strerror(
   int errnum );

char * _strerror(
   const char *strErrMsg );

wchar_t * _wcserror(
   int errnum );

wchar_t * __wcserror(
   const wchar_t *strErrMsg );
```

### <a name="parameters"></a>Parametry

*errnum*\
Numer błędu.

*strErrMsg*\
Wiadomość dostarczona przez użytkownika.

## <a name="return-value"></a>Wartość zwracana

Wszystkie te funkcje zwracają wskaźnik do ciągu komunikatu o błędzie w buforze magazynu lokalnego wątku należącym do środowiska uruchomieniowego. Późniejsze wywołania w tym samym wątku mogą zastąpić ten ciąg.

## <a name="remarks"></a>Uwagi

Funkcja **strerror** mapuje *errnum* na ciąg komunikatu o błędzie i zwraca wskaźnik do ciągu. Funkcje **strerror** i **_strerror** nie drukują wiadomości. Aby drukować, wywołaj funkcję wyjściową, taką jak [fprintf —](fprintf-fprintf-l-fwprintf-fwprintf-l.md):

```C
if (( _access( "datafile", 2 )) == -1 )
   fprintf( stderr, _strerror(NULL) );
```

Jeśli *strErrMsg* jest przenoszona jako **null**, **_strerror** zwraca wskaźnik do ciągu. Zawiera komunikat o błędzie systemu dla ostatniego wywołania biblioteki, które spowodowało wystąpienie błędu. Ciąg komunikatu o błędzie jest zakończony znakiem nowego wiersza ("\n"). Gdy *strErrMsg* nie ma **wartości null**, ciąg zawiera, w kolejności: ciąg *strErrMsg* , dwukropek, spacja, komunikat o błędzie systemowy i znak nowego wiersza. Komunikat ciągu może mieć długość maksymalnie 94 znaków, w wąskich ( **_strerror**) lub szerokich ( **__wcserror**) znakach.

Rzeczywisty numer błędu dla **_strerror** jest przechowywany w zmiennej [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Aby wygenerować dokładne wyniki, wywołaj **_strerror** natychmiast po procedurze biblioteki zwraca błąd. W przeciwnym razie późniejsze wywołania procedur biblioteki mogą zastąpić wartość **errno** .

**_wcserror** i **__wcserror** są odpowiednio wersjami **strerror** i **_strerror**.

**_strerror**, **_wcserror**i **__Wcserror** są charakterystyczne dla firmy Microsoft, a nie częścią standardowej biblioteki C. Nie zalecamy korzystania z nich w przypadku, gdy potrzebny jest kod przenośny. W przypadku standardowej zgodności C zamiast tego należy użyć **strerror** .

Aby uzyskać ciągi błędów, zalecamy **strerror** lub **_wcserror** zamiast przestarzałych makr [_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) i [_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) oraz przestarzałych funkcji wewnętrznych **__sys_errlist** i **__sys_nerr**.

### <a name="generic-text-routine-mappings"></a>Mapowania procedury tekstu ogólnego

|Procedura TCHAR.H|Nie zdefiniowano _MBCS _UNICODE &|_MBCS zdefiniowano|_UNICODE zdefiniowano|
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

\ [manipulowania ciągami](../../c-runtime-library/string-manipulation-crt.md)
[clearerr](clearerr.md)\
\ [odwołującego](ferror.md)
[perror, _wperror](perror-wperror.md)
