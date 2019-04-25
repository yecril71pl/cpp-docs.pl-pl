---
title: _access_s, _waccess_s
ms.date: 11/04/2016
apiname:
- _access_s
- _waccess_s
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
- waccess_s
- access_s
- _waccess_s
- _access_s
helpviewer_keywords:
- access_s function
- taccess_s function
- _taccess_s function
- waccess_s function
- _access_s function
- _waccess_s function
ms.assetid: fb3004fc-dcd3-4569-8b27-d817546e947e
ms.openlocfilehash: 17d19527323f3e97edecd22ca7c0a0262b1cfbad
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62335688"
---
# <a name="accesss-waccesss"></a>_access_s, _waccess_s

Określa uprawnienia odczytu/zapisu pliku. To jest wersja [_access, _waccess —](access-waccess.md) ze wzmocnieniem zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
errno_t _access_s(
   const char *path,
   int mode
);
errno_t _waccess_s(
   const wchar_t *path,
   int mode
);
```

### <a name="parameters"></a>Parametry

*Ścieżka*<br/>
Ścieżka pliku lub katalogu.

*Tryb*<br/>
Ustawienie uprawnienia.

## <a name="return-value"></a>Wartość zwracana

Każda funkcja zwraca 0, jeśli plik ma w danym trybie. Funkcja zwraca kod błędu, jeśli plik o nazwie nie istnieje lub nie jest dostępna w danym trybie. W takim przypadku funkcja zwraca kod błędu z zestawu w następujący sposób, a także ustawia `errno` taką samą wartość.

|errno wartość|Warunek|
|-|-|
`EACCES`|Odmowa dostępu. Ustawienie uprawnienia pliku zezwalają na dostęp określonym.
`ENOENT`|Nazwa pliku lub nie można odnaleźć ścieżki.
`EINVAL`|Nieprawidłowy parametr.

Aby uzyskać więcej informacji, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Gdy jest używana z plikami, **_access_s —** funkcja określa, czy określony plik istnieje i czy może być dostępna jako określony przez wartość *tryb*. Gdy jest używana z katalogami, **_access_s —** określa jedynie, czy istnieje określony katalog. Windows 2000 i nowszych systemach operacyjnych, wszystkie katalogi ma uprawnienia odczytu i zapisu.

|wartość trybu|Plik kontroli|
|----------------|---------------------|
|00|Istnienie tylko.|
|02|Uprawnienie do zapisu.|
|04|Uprawnienia do odczytu.|
|06|Uprawnienia odczytu i zapisu.|

Uprawnienia do odczytu lub zapisu pliku nie jest wystarczająco, aby zapewnić możliwość otwarcia pliku. Na przykład, jeśli plik jest zablokowany przez inny proces, może nie być dostępne nawet jeśli **_access_s —** zwraca wartość 0.

**_waccess_s —** to wersja znaku dwubajtowego **_access_s —**, gdzie *ścieżki* argument **_waccess_s —** jest ciągiem znaku dwubajtowego. W przeciwnym razie **_waccess_s —** i **_access_s —** zachowują się identycznie.

Te funkcje sprawdzają poprawność swoich parametrów. Jeśli *ścieżki* ma wartość NULL lub *tryb* nie określa prawidłowego trybu wywołany nieprawidłowy parametr uchwytu, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje ustawiają `errno` do `EINVAL` i zwracają `EINVAL`.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|`_taccess_s`|**_access_s**|**_access_s**|**_waccess_s**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|---------------------|
|**_access_s**|\<io.h>|\<errno.h>|
|**_waccess_s**|\<WChar.h > lub \<io.h >|\<errno.h>|

## <a name="example"></a>Przykład

W tym przykładzie użyto **_access_s —** można znaleźć w pliku o nazwie crt_access_s.c, aby zobaczyć, czy istnieje i czy jest dozwolone zapisywanie.

```C
// crt_access_s.c

#include <io.h>
#include <stdio.h>
#include <stdlib.h>

int main( void )
{
    errno_t err = 0;

    // Check for existence.
    if ((err = _access_s( "crt_access_s.c", 0 )) == 0 )
    {
        printf_s( "File crt_access_s.c exists.\n" );

        // Check for write permission.
        if ((err = _access_s( "crt_access_s.c", 2 )) == 0 )
        {
            printf_s( "File crt_access_s.c does have "
                      "write permission.\n" );
        }
        else
        {
            printf_s( "File crt_access_s.c does not have "
                      "write permission.\n" );
        }
    }
    else
    {
        printf_s( "File crt_access_s.c does not exist.\n" );
    }
}
```

```Output
File crt_access_s.c exists.
File crt_access_s.c does not have write permission.
```

## <a name="see-also"></a>Zobacz także

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
[_access, _waccess](access-waccess.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_stat, _wstat — funkcje](stat-functions.md)