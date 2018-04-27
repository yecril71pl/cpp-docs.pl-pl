---
title: perror, _wperror — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
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
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3f6be77354f4efa1485f32ed178dc68b594b4f75
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="perror-wperror"></a>perror, _wperror

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

*komunikat* ciąg komunikatu do drukowania.

## <a name="remarks"></a>Uwagi

**Perror** funkcja wyświetla komunikat o błędzie **stderr**. **_wperror —** jest wersja znaków dwubajtowych **_perror**; *komunikat* argument **_wperror —** jest ciągiem znaków dwubajtowych. **_wperror —** i **_perror** zachowują się tak samo w przeciwnym razie wartość.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tperror —**|**perror**|**perror**|**_wperror —**|

*komunikat* drukowania najpierw, a następnie dwukropek, a następnie system komunikat o błędzie dla ostatniego wywołania biblioteki, które spowodowało błąd, a na końcu znakiem nowego wiersza. Jeśli *komunikat* wskaźnika o wartości null lub wskaźnikiem do ciągu wartości null, **perror** wyświetla tylko system komunikat o błędzie.

Numer błędu jest przechowywana w zmiennej [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) (zdefiniowany w numer błędu. H). Komunikaty o błędach systemu są dostępne za pośrednictwem zmiennej [_sys_errlist —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md), która jest tablicę komunikatów uporządkowanych według numer błędu. **perror** drukuje wiadomości odpowiednie błąd przy użyciu **errno** wartość jako indeks **_sys_errlist —**. Wartość zmiennej [_sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) jest zdefiniowany jako maksymalną liczbę elementów w **_sys_errlist —** tablicy.

Aby uzyskać dokładne wyniki wywołania **perror** natychmiast po procedury biblioteki zwraca błąd. W przeciwnym razie można zastąpić wezwań **errno** wartości.

W oknach systemu operacyjnego, niektóre **errno** wartości na liście numer błędu. H są używane. Wartości te są zarezerwowane do użytku przez system operacyjny UNIX. Zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) listę **errno** wartości używane przez system operacyjny Windows. **perror** wyświetla pusty ciąg dla każdego **errno** wartości nie są używane przez tych platform.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**perror**|\<stdio.h > lub \<stdlib.h >|
|**_wperror —**|\<stdio.h > lub \<wchar.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).

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
