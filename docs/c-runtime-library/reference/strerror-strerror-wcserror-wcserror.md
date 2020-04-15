---
title: strerror, _strerror, _wcserror, __wcserror
description: W tym artykule opisano funkcje programu Microsoft C Runtime Library (CRT), _strerror, _wcserror i __wcserror.
ms.date: 4/2/2020
api_name:
- strerror
- _strerror
- _wcserror
- __wcserror
- _o___wcserror
- _o__strerror
- _o__wcserror
- _o_strerror
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 9eecb7376cf476f0128dc20c8884746a3b4d47d9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337328"
---
# <a name="strerror-_strerror-_wcserror-__wcserror"></a>strerror, _strerror, _wcserror, __wcserror

Pobiera ciąg komunikatu o błędzie systemu **(strerror**, **_wcserror**) lub formatuje podany przez użytkownika ciąg komunikatu o błędzie (**_strerror**, **__wcserror**). Dostępne są bezpieczniejsze wersje tych funkcji; [zobacz strerror_s, _strerror_s, \__wcserror_s, _wcserror_s](strerror-s-strerror-s-wcserror-s-wcserror-s.md).

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

*errnum ( errnum )*\
Numer błędu.

*strErrMsg*\
Komunikat dostarczony przez użytkownika.

## <a name="return-value"></a>Wartość zwracana

Wszystkie te funkcje zwracają wskaźnik do ciągu komunikatu o błędzie w buforze magazynu lokalnego wątku należącego do środowiska wykonawczego. Później wywołania w tym samym wątku można zastąpić ten ciąg.

## <a name="remarks"></a>Uwagi

Funkcja **strerror** mapuje *errnum* do ciągu komunikatu o błędzie i zwraca wskaźnik do ciągu. Funkcje **strerror** i **_strerror** nie drukują wiadomości. Aby wydrukować, należy wywołać funkcję wyjścia, taką jak [fprintf:](fprintf-fprintf-l-fwprintf-fwprintf-l.md)

```C
if (( _access( "datafile", 2 )) == -1 )
   fprintf( stderr, _strerror(NULL) );
```

Jeśli *strErrMsg* jest przekazywana jako **NULL**, **_strerror** zwraca wskaźnik do ciągu. Zawiera komunikat o błędzie systemu dla ostatniego wywołania biblioteki, który spowodował błąd. Ciąg komunikatu o błędzie jest kończony przez znak nowego typu ('\n'). Gdy *strErrMsg* nie jest **null**, ciąg zawiera, w kolejności: *strErrMsg* ciąg, dwukropek, spacja, komunikat o błędzie systemu i znak nowego rzędu. Wiadomość ciągu może mieć co najwyżej 94 znaki, w postaci wąskiej **(_strerror)** lub szerokiej (**__wcserror).**

Rzeczywisty numer błędu dla **_strerror** jest przechowywany w zmiennej [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Aby uzyskać dokładne wyniki, wywołaj **_strerror** natychmiast po rutynowych biblioteki zwraca błąd. W przeciwnym razie późniejsze wywołania procedur biblioteki może zastąpić wartość **errno.**

**_wcserror** i **__wcserror** są szerokoznakowymi wersjami **strerror** i **_strerror,** odpowiednio.

**_strerror** **, _wcserror**i **__wcserror** są specyficzne dla firmy Microsoft, a nie są częścią biblioteki Standard C. Nie zalecamy używania ich tam, gdzie chcesz przenośny kod. W przypadku zgodności ze standardem C należy użyć **strerror.**

Aby uzyskać ciągi błędów, zaleca się **strerror** lub **_wcserror** zamiast przestarzałych makr [_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) i [_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) oraz przestarzałe funkcje wewnętrzne **__sys_errlist** i **__sys_nerr**.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania rutynowych tekstu ogólnego

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcserror**|**strerror**|**strerror**|**_wcserror**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**strerror**|\<string.h>|
|**_strerror**|\<string.h>|
|**_wcserror** **, __wcserror**|\<string.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [perror](perror-wperror.md).

## <a name="see-also"></a>Zobacz też

[Manipulacja ciągami](../../c-runtime-library/string-manipulation-crt.md)\
[jaśniejsze](clearerr.md)\
[ferror](ferror.md)\
[perror, _wperror](perror-wperror.md)
