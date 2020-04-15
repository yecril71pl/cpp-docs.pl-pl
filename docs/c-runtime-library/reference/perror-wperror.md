---
title: perror, _wperror
ms.date: 4/2/2020
api_name:
- _wperror
- perror
- _o__wperror
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
ms.openlocfilehash: 0c50e77863b4b136ac59b6f79d8e529691032609
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338531"
---
# <a name="perror-_wperror"></a>perror, _wperror

Drukowanie komunikatu o błędzie.

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

*Komunikat*<br/>
Komunikat ciąg do wydrukowania.

## <a name="remarks"></a>Uwagi

Funkcja **perror** drukuje komunikat o błędzie do **stderr**. **_wperror** jest szerokoznakową wersją **_perror**; argument *message* do **_wperror** jest ciągiem znaków o szerokim charakterze. **_wperror** i **_perror** zachowują się identycznie w przeciwnym razie.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tperror**|**Perror**|**Perror**|**_wperror**|

*komunikat* jest drukowany najpierw, a następnie dwukropek, następnie przez komunikat o błędzie systemu dla ostatniego wywołania biblioteki, które spowodowało błąd, a na koniec przez znak nowego linii. Jeśli *wiadomość* jest wskaźnikiem zerowym lub wskaźnikiem do ciągu zerowego, **perror** drukuje tylko komunikat o błędzie systemu.

Numer błędu jest przechowywany w zmiennej [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) (zdefiniowanej w ERRNO. H). Komunikaty o błędach systemu są dostępne za pośrednictwem zmiennej [_sys_errlist](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md), która jest tablicą komunikatów uporządkowanych według numeru błędu. **perror** drukuje odpowiedni komunikat o błędzie przy użyciu wartości **errno** jako indeksu do **_sys_errlist**. Wartość [zmiennej _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) jest definiowana jako maksymalna liczba elementów w tablicy **_sys_errlist.**

Aby uzyskać dokładne wyniki, wywołaj **perror** natychmiast po powrocie rutynowych biblioteki z błędem. W przeciwnym razie kolejne wywołania mogą zastąpić wartość **errno.**

W systemie operacyjnym Windows niektóre wartości **errno** wymienione w ERRNO. H są nieużywane. Te wartości są zarezerwowane do użytku przez system operacyjny UNIX. Zobacz [_doserrno, errno, _sys_errlist i _sys_nerr,](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) aby uzyskać listę wartości **errno** używanych przez system operacyjny Windows. **perror** drukuje pusty ciąg dla dowolnej wartości **errno** nie używanej przez te platformy.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**Perror**|\<stdio.h> lub \<stdlib.h>|
|**_wperror**|\<stdio.h> lub \<wchar.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek wyładowywowych języka C](../../c-runtime-library/crt-library-features.md).

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

## <a name="see-also"></a>Zobacz też

[Kontrola procesu i środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[clearerr](clearerr.md)<br/>
[ferror](ferror.md)<br/>
[_strerror, _wcserror, \__wcserror](strerror-strerror-wcserror-wcserror.md)<br/>
