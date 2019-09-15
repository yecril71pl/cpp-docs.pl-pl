---
title: perror, _wperror
ms.date: 11/04/2016
api_name:
- _wperror
- perror
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
- _wperror
- _tperror
- perror
helpviewer_keywords:
- _tperror function
- tperror function
- wperror function
- error messages, printing
- printing error messages
- _wperror function
- perror function
ms.assetid: 34fce792-16fd-4673-9849-cd88b54b6cd5
ms.openlocfilehash: 755b638f320fcc583faecfe6aa82269e4e1b3d8f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951035"
---
# <a name="perror-_wperror"></a>perror, _wperror

Drukuj komunikat o błędzie.

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
Komunikat ciągu do wydrukowania.

## <a name="remarks"></a>Uwagi

Funkcja **pError** drukuje komunikat o błędzie do **stderr**. **_wperror** to dwubajtowa wersja **_perror**; argumentem *komunikatu* **_wperror** jest ciąg znaków dwubajtowych. **_wperror** i **_perror** zachowują się identycznie w inny sposób.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _UNICODE & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tperror**|**pError**|**pError**|**_wperror**|

*komunikat* jest drukowany po raz pierwszy, po którym następuje dwukropek, następnie komunikat o błędzie systemu dla ostatniego wywołania biblioteki, które wygenerowało błąd, i na koniec przez znak nowego wiersza. Jeśli *komunikat* jest wskaźnikiem typu null lub wskaźnikiem do ciągu o wartości null, **pError** drukuje tylko komunikat o błędzie systemowym.

Numer błędu jest przechowywany w zmiennej [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) (zdefiniowanej w errno. H). Do komunikatów o błędach systemu uzyskuje się dostęp za pomocą zmiennej [_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md), która jest tablicą komunikatów uporządkowanych według numeru błędu. **pError** drukuje odpowiedni komunikat o błędzie przy użyciu wartości **errno** jako indeksu do **_sys_errlist**. Wartość zmiennej [_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) jest definiowana jako maksymalna liczba elementów w tablicy **_sys_errlist** .

Aby uzyskać dokładne wyniki, należy wywołać **pError** natychmiast po wykonaniu procedury biblioteki z błędem. W przeciwnym razie kolejne wywołania mogą zastąpić wartość **errno** .

W systemie operacyjnym Windows niektóre wartości **errno** wymienione w errno. H nie jest używane. Te wartości są zarezerwowane do użytku przez system operacyjny UNIX. Zobacz [_doserrno, errno, _sys_errlist i _sys_nerr,](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) aby zapoznać się z listą wartości **errno** używanych przez system operacyjny Windows. **pError** drukuje pusty ciąg dla dowolnej wartości **errno** , która nie jest używana przez te platformy.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**pError**|\<stdio. h > lub \<STDLIB. h >|
|**_wperror**|\<stdio. h > lub \<WCHAR. h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek uruchomieniowych języka C](../../c-runtime-library/crt-library-features.md).

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
