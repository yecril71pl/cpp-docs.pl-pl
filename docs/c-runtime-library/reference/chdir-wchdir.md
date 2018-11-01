---
title: _chdir, _wchdir
ms.date: 11/04/2016
apiname:
- _wchdir
- _chdir
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
- tchdir
- _chdir
- _wchdir
- _tchdir
- wchdir
helpviewer_keywords:
- _tchdir function
- _chdir function
- _wchdir function
- tchdir function
- wchdir function
- chdir function
- directories [C++], changing
ms.assetid: 85e9393b-62ac-45d5-ab2a-fa2217f6152e
ms.openlocfilehash: e4cf7a44864df0b5ecca531aab3db4546c25bb2c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50556341"
---
# <a name="chdir-wchdir"></a>_chdir, _wchdir

Zmienia bieżący katalog roboczy.

## <a name="syntax"></a>Składnia

```C
int _chdir(
   const char *dirname
);
int _wchdir(
   const wchar_t *dirname
);
```

### <a name="parameters"></a>Parametry

*nazwa_kat*<br/>
Ścieżka do nowego katalogu roboczego.

## <a name="return-value"></a>Wartość zwracana

Te funkcje zwracają wartość 0, jeśli kończy się pomyślnie. Zwracana wartość-1 wskazuje błąd. Jeśli nie można odnaleźć określonej ścieżki, **errno** ustawiono **ENOENT**. Jeśli *nazwa_kat* jest **NULL**, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **errno** ustawiono **EINVAL** a funkcja zwraca wartość -1.

## <a name="remarks"></a>Uwagi

**_Chdir —** funkcji zmienia bieżący katalog roboczy do katalogu określonego przez *nazwa_kat*. *Nazwa_kat* parametru musi odwoływać się do istniejącego katalogu. Tę funkcję można zmienić bieżący katalog roboczy na dowolnym dysku. Jeśli litera dysku została określona w *nazwa_kat*, również zmiany domyślną literę dysku. Na przykład jeśli jest domyślną literę dysku i \BIN jest bieżący katalog roboczy, poniższe wywołanie zmienia bieżący katalog roboczy na dysku C i ustanawia C jako nowego dysku domyślne:

```C
_chdir("c:\temp");
```

Jeśli używasz opcjonalne ukośnika odwrotnego (**&#92;**) w ścieżkach, należy umieścić dwa ukośniki odwrotne (**&#92;&#92;**) ciągu języka C do reprezentowania pojedynczy ukośnik odwrotny ( **&#92;**).

**_wchdir —** to wersja znaku dwubajtowego **_chdir —**; *nazwa_kat* argument **_wchdir —** jest ciągiem znaku dwubajtowego. **_wchdir —** i **_chdir —** zachowują się identycznie.

### <a name="generic-text-routine-mapping"></a>Mapowania procedur zwykłego tekstu:

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tchdir —**|**_chdir**|**_chdir**|**_wchdir**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|---------------------|
|**_chdir**|\<direct.h>|\<errno.h>|
|**_wchdir**|\<Direct.h > lub \<wchar.h >|\<errno.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_chdir.c
// arguments: C:\WINDOWS

/* This program uses the _chdir function to verify
   that a given directory exists. */

#include <direct.h>
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>

int main( int argc, char *argv[] )
{

   if(_chdir( argv[1] ) )
   {
      switch (errno)
      {
      case ENOENT:
         printf( "Unable to locate the directory: %s\n", argv[1] );
         break;
      case EINVAL:
         printf( "Invalid buffer.\n");
         break;
      default:
         printf( "Unknown error.\n");
      }
   }
   else
      system( "dir *.exe");
}
```

```Output
Volume in drive C has no label.
Volume Serial Number is 2018-08A1

Directory of c:\windows

08/29/2002  04:00 AM         1,004,032 explorer.exe
12/17/2002  04:43 PM            10,752 hh.exe
03/03/2003  09:24 AM            33,792 ieuninst.exe
10/29/1998  04:45 PM           306,688 IsUninst.exe
08/29/2002  04:00 AM            66,048 NOTEPAD.EXE
03/03/2003  09:24 AM            33,792 Q330994.exe
08/29/2002  04:00 AM           134,144 regedit.exe
02/28/2003  06:26 PM            46,352 setdebug.exe
08/29/2002  04:00 AM            15,360 TASKMAN.EXE
08/29/2002  04:00 AM            49,680 twunk_16.exe
08/29/2002  04:00 AM            25,600 twunk_32.exe
08/29/2002  04:00 AM           256,192 winhelp.exe
08/29/2002  04:00 AM           266,752 winhlp32.exe
              13 File(s)      2,249,184 bytes
               0 Dir(s)  67,326,029,824 bytes free
```

## <a name="see-also"></a>Zobacz także

[Kontrola katalogu](../../c-runtime-library/directory-control.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_rmdir, _wrmdir](rmdir-wrmdir.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
