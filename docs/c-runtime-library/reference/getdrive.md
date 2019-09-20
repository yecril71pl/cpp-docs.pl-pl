---
title: _getdrive
ms.date: 09/19/2019
api_name:
- _getdrive
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _getdrive
- getdrive
helpviewer_keywords:
- current disk drive
- getdrive function
- disk drives
- _getdrive function
ms.assetid: e40631a0-8f1a-4897-90ac-e1037ff30bca
ms.openlocfilehash: 94d6c15270827cf61ec6086de8fa11251b435e2c
ms.sourcegitcommit: f907b15f50a6b945d0b87c03af0050946157d701
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/20/2019
ms.locfileid: "71158764"
---
# <a name="_getdrive"></a>_getdrive

Pobiera bieżący dysk.

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
int _getdrive( void );
```

## <a name="return-value"></a>Wartość zwracana

Zwraca bieżący (domyślny) dysk (1 = A, 2 = B i tak dalej). Wartość zwracana przez zero oznacza, że bieżąca ścieżka nie zaczyna się od nazwy dysku literowego, na przykład ścieżki UNC. Lub oznacza to, że wewnętrzny przydział buforu nie powiódł się. Jeśli wewnętrzna alokacja nie powiedzie się, `errno` jest ustawiona na ENOMEM.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_getdrive**|\<direct.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_getdrive.c
// compile with: /c
// Illustrates drive functions including:
//    _getdrive       _chdrive        _getdcwd
//

#include <stdio.h>
#include <direct.h>
#include <stdlib.h>
#include <ctype.h>

int main( void )
{
   int ch, drive, curdrive;
   static char path[_MAX_PATH];

   // Save current drive.
   curdrive = _getdrive();

   printf( "Available drives are:\n" );

   // If we can switch to the drive, it exists.
   for( drive = 1; drive <= 26; drive++ )
   {
      if( !_chdrive( drive ) )
      {
         printf( "%c:", drive + 'A' - 1 );
         if( _getdcwd( drive, path, _MAX_PATH ) != NULL )
            printf( " (Current directory is %s)", path );
         putchar( '\n' );
      }
   }

   // Restore original drive.
   _chdrive( curdrive );
}
```

```Output
Available drives are:
A: (Current directory is A:\)
C: (Current directory is C:\)
E: (Current directory is E:\testdir\bin)
F: (Current directory is F:\)
G: (Current directory is G:\)
```

## <a name="see-also"></a>Zobacz także

[Kontrola katalogu](../../c-runtime-library/directory-control.md)<br/>
[_chdrive](chdrive.md)<br/>
[_getcwd, _wgetcwd](getcwd-wgetcwd.md)<br/>
[_getdcwd, _wgetdcwd](getdcwd-wgetdcwd.md)<br/>
