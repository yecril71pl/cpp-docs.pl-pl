---
title: perror, _wperror — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wperror
- perror
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
- _wperror
- _tperror
- perror
dev_langs:
- C++
helpviewer_keywords:
- _tperror function
- tperror function
- wperror function
- error messages, printing
- printing error messages
- _wperror function
- perror function
ms.assetid: 34fce792-16fd-4673-9849-cd88b54b6cd5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1df9e064ac7af761a858c6e18d99526a9b3c7ffb
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44103791"
---
# <a name="perror-wperror"></a>perror, _wperror

Wydrukuj komunikat o błędzie.

## <a name="syntax"></a>Składnia

```C
void perror(
   const char *message
);
void _wperror(
   const wchar_t *message
);
```

### <a name="parameters"></a>Parametry

*komunikat*<br/>
Ciąg komunikatu do drukowania.

## <a name="remarks"></a>Uwagi

**Perror** funkcja drukuje komunikat o błędzie do **stderr**. **_wperror —** to wersja znaku dwubajtowego **_perror**; *komunikat* argument **_wperror —** jest ciągiem znaku dwubajtowego. **_wperror —** i **_perror** zachowują się identycznie.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tperror —**|**perror**|**perror**|**_wperror —**|

*komunikat* najpierw, wydrukowaniu, a następnie dwukropek, a następnie komunikat o błędzie systemu dla ostatniego wywołania biblioteki, które spowodowało błąd, a na koniec znakiem nowego wiersza. Jeśli *komunikat* jest wskaźnikiem typu null lub wskaźnikiem do ciągu o wartości null, **perror** drukuje tylko system komunikat o błędzie.

Numer błędu jest przechowywana w zmiennej [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) (zdefiniowany w numer błędu. GODZ.). Komunikaty o błędach systemu są dostępne za pośrednictwem zmiennej [_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md), który jest tablicą wiadomości według wielkości błędu. **perror** wyświetli odpowiedni komunikat o błędzie komunikat przy użyciu **errno** wartość jako indeksu do **_sys_errlist**. Wartość zmiennej [_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) jest zdefiniowana jako maksymalna liczba elementów w **_sys_errlist** tablicy.

Aby uzyskać dokładne wyniki, należy wywołać **perror** natychmiast, po procedurze biblioteki zwraca błąd. W przeciwnym razie kolejnych wywołań może spowodować zastąpienie **errno** wartości.

W Windows system operacyjny, niektóre **errno** wartości na liście numer błędu. H są nieużywane. Te wartości są zarezerwowane do użytku przez system operacyjny UNIX. Zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) listę **errno** wartości używane przez system operacyjny Windows. **perror** drukuje pusty ciąg dla każdego **errno** wartość nie jest używana przez te platformy.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**perror**|\<stdio.h > lub \<stdlib.h >|
|**_wperror —**|\<stdio.h > lub \<wchar.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawczej C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Przykład

```C
// crt_perror.c
// compile with: /W3
/* This program attempts to open a file named
* NOSUCHF.ILE. Because this file probably doesn't exist,
* an error message is displayed. The same message is
* created using perror, strerror, and _strerror.
*/

#include <fcntl.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <io.h>
#include <stdlib.h>
#include <stdio.h>
#include <string.h>
#include <share.h>

int main( void )
{
   int  fh;

   if( _sopen_s( &fh, "NOSUCHF.ILE", _O_RDONLY, _SH_DENYNO, 0 ) != 0 )
   {
      /* Three ways to create error message: */
      perror( "perror says open failed" );
      printf( "strerror says open failed: %s\n",
         strerror( errno ) ); // C4996
      printf( _strerror( "_strerror says open failed" ) ); // C4996
      // Note: strerror and _strerror are deprecated; consider
      // using strerror_s and _strerror_s instead.
   }
   else
   {
      printf( "open succeeded on input file\n" );
      _close( fh );
   }
}
```

```Output
perror says open failed: No such file or directory
strerror says open failed: No such file or directory
_strerror says open failed: No such file or directory
```

## <a name="see-also"></a>Zobacz także

[Procedury kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[clearerr](clearerr.md)<br/>
[ferror](ferror.md)<br/>
[strerror, _strerror, _wcserror, \__wcserror](strerror-strerror-wcserror-wcserror.md)<br/>
