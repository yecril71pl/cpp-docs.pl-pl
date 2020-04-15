---
title: _mkdir, _wmkdir
ms.date: 4/2/2020
api_name:
- _wmkdir
- _mkdir
- _o__mkdir
- _o__wmkdir
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
- api-ms-win-crt-filesystem-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mkdir
- tmkdir
- _tmkdir
- wmkdir
- _wmkdir
helpviewer_keywords:
- _wmkdir function
- folders [C++], creating
- wmkdir function
- directories [C++], creating
- mkdir function
- tmkdir function
- _mkdir function
- _tmkdir function
ms.assetid: 7f22d01d-63a5-4712-a6e7-d34878b2d840
ms.openlocfilehash: 56e525dd765ff2594eebcfe9a0aed37670b12e3e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338782"
---
# <a name="_mkdir-_wmkdir"></a>_mkdir, _wmkdir

Tworzy nowy katalog.

## <a name="syntax"></a>Składnia

```C

int _mkdir(
   const char *dirname
);
int _wmkdir(
   const wchar_t *dirname
);
```

### <a name="parameters"></a>Parametry

*dirname (dirname)*<br/>
Ścieżka dla nowego katalogu.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca wartość 0, jeśli utworzono nowy katalog. W razie błędu funkcja zwraca wartość -1 i ustawia **errno** w następujący sposób.

**EEXIST (EEXIST)** Katalog nie został utworzony, ponieważ *dirname* jest nazwą istniejącego pliku, katalogu lub urządzenia.

**ENOENT ( ENOENT )** Nie znaleziono ścieżki.

Aby uzyskać więcej informacji na temat tych i innych kodów zwrotnych, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Funkcja **_mkdir** tworzy nowy katalog z określonym *dirname.* **_mkdir** można utworzyć tylko jeden nowy katalog na wywołanie, więc tylko ostatni składnik *dirname* może nadać nazwę nowemu katalogowi. **_mkdir** nie tłumaczy ograniczników ścieżki. W systemie Windows NT zarówno \\ukośnik odwrotny ( ) i ukośnik do przodu (/ ) są prawidłowymi ogranicznikami ścieżki w ciągach znaków w procedurach wykonywania.

**_wmkdir** jest szerokoznakową wersją **_mkdir**; *argumentem dirname* **do _wmkdir** jest ciągiem znaków o szerokim charakterze. **_wmkdir** i **_mkdir** zachowują się identycznie w przeciwnym razie.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmkdir**|**_mkdir**|**_mkdir**|**_wmkdir**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_mkdir**|\<direct.h>|
|**_wmkdir**|\<direct.h> lub \<wchar.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek wyładowywowych języka C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Przykład

```C
// crt_makedir.c

#include <direct.h>
#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   if( _mkdir( "\\testtmp" ) == 0 )
   {
      printf( "Directory '\\testtmp' was successfully created\n" );
      system( "dir \\testtmp" );
      if( _rmdir( "\\testtmp" ) == 0 )
        printf( "Directory '\\testtmp' was successfully removed\n"  );
      else
         printf( "Problem removing directory '\\testtmp'\n" );
   }
   else
      printf( "Problem creating directory '\\testtmp'\n" );
}
```

### <a name="sample-output"></a>Przykładowe dane wyjściowe

```Output
Directory '\testtmp' was successfully created
Volume in drive C has no label.
Volume Serial Number is E078-087A

Directory of C:\testtmp

02/12/2002  09:56a      <DIR>          .
02/12/2002  09:56a      <DIR>          ..
               0 File(s)              0 bytes
               2 Dir(s)  15,498,690,560 bytes free
Directory '\testtmp' was successfully removed
```

## <a name="see-also"></a>Zobacz też

[Kontrola katalogu](../../c-runtime-library/directory-control.md)<br/>
[_chdir, _wchdir](chdir-wchdir.md)<br/>
[_rmdir, _wrmdir](rmdir-wrmdir.md)<br/>
