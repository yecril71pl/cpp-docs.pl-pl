---
title: _mkdir —, _wmkdir — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wmkdir
- _mkdir
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
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _mkdir
- tmkdir
- _tmkdir
- wmkdir
- _wmkdir
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 40641911af9c61285049a5943cdc8f5c21cba99b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32402143"
---
# <a name="mkdir-wmkdir"></a>_mkdir, _wmkdir

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

*DirName*<br/>
Ścieżka dla nowego katalogu.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca wartość 0, jeśli nowy katalog został utworzony. Wystąpił błąd, funkcja zwraca wartość -1 i zestawy **errno** w następujący sposób.

**Eexist —** katalog nie został utworzony, ponieważ *dirname* jest nazwą istniejącego pliku, katalogu lub urządzenia.

**Enoent —** nie znaleziono ścieżki.

Aby uzyskać więcej informacji na temat tych i innych kody powrotu, zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**_Mkdir —** funkcja tworzy nowy katalog z określonym *dirname.* **_mkdir —** można utworzyć tylko jeden nowy katalog na wywołanie, dlatego tylko ostatni składnik *dirname* określić nazwę nowego katalogu. **_mkdir —** nie tłumaczy ogranicznik ścieżki. W systemie Windows NT, zarówno ukośnik odwrotny ( \\) i ukośnika (/) są ograniczniki prawidłową ścieżkę w ciągów znaków w czasie wykonywania procedury.

**_wmkdir —** jest wersja znaków dwubajtowych **_mkdir —**; *dirname* argument **_wmkdir —** jest ciągiem znaków dwubajtowych. **_wmkdir —** i **_mkdir —** zachowują się tak samo w przeciwnym razie wartość.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmkdir —**|**_mkdir**|**_mkdir**|**_wmkdir**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_mkdir**|\<direct.h>|
|**_wmkdir**|\<Direct.h > lub \<wchar.h >|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).

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

## <a name="see-also"></a>Zobacz także

[Kontrola katalogu](../../c-runtime-library/directory-control.md)<br/>
[_chdir, _wchdir](chdir-wchdir.md)<br/>
[_rmdir, _wrmdir](rmdir-wrmdir.md)<br/>
