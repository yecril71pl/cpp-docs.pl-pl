---
title: _access_s, _waccess_s
ms.date: 4/2/2020
api_name:
- _access_s
- _waccess_s
- _o__access_s
- _o__waccess_s
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
ms.openlocfilehash: 7f16951b99eb29bcb8c39499c29be1018cb86616
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81349123"
---
# <a name="_access_s-_waccess_s"></a>_access_s, _waccess_s

Określa uprawnienia do odczytu/zapisu pliku. Jest to wersja [_access, _waccess](access-waccess.md) z ulepszeniami zabezpieczeń, jak opisano w [funkcji zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Ustawienie uprawnień.

## <a name="return-value"></a>Wartość zwracana

Każda funkcja zwraca wartość 0, jeśli plik ma dany tryb. Funkcja zwraca kod błędu, jeśli nazwany plik nie istnieje lub nie jest dostępny w danym trybie. W takim przypadku funkcja zwraca kod błędu z zestawu `errno` w następujący sposób, a także ustawia tę samą wartość.

|wartość errno|Warunek|
|-|-|
`EACCES`|Odmowa dostępu. Ustawienie uprawnień pliku nie zezwala na określony dostęp.
`ENOENT`|Nie znaleziono nazwy pliku lub ścieżki.
`EINVAL`|Nieprawidłowy parametr.

Aby uzyskać więcej informacji, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

W przypadku użycia z plikami funkcja **_access_s** określa, czy określony plik istnieje i można uzyskać do niego dostęp zgodnie z wartością *trybu*. W przypadku użycia z katalogami **_access_s** określa tylko, czy określony katalog istnieje. W systemach operacyjnych Windows 2000 i nowszych wszystkie katalogi mają dostęp do odczytu i zapisu.

|wartość trybu|Sprawdza plik dla|
|----------------|---------------------|
|00|Tylko istnienie.|
|02|Uprawnienie do zapisu.|
|04|Uprawnienie do odczytu.|
|06|Uprawnienie do odczytu i zapisu.|

Uprawnienie do odczytu lub zapisu pliku nie wystarczy, aby zapewnić możliwość otwarcia pliku. Na przykład jeśli plik jest zablokowany przez inny proces, może nie być dostępny, nawet **jeśli _access_s** zwraca 0.

**_waccess_s** jest szerokoznakową wersją **_access_s**, gdzie argument *ścieżki* do **_waccess_s** jest ciągiem znaków o szerokim charakterze. W przeciwnym razie **_waccess_s** i **_access_s** zachowywać się identycznie.

Te funkcje sprawdzają ich parametry. Jeśli *ścieżka* ma wartość NULL lub *tryb* nie określa prawidłowego trybu, wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w obszarze Sprawdzanie [poprawności parametrów.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, te `errno` funkcje są ustawione na `EINVAL` i zwraca. `EINVAL`

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|`_taccess_s`|**_access_s**|**_access_s**|**_waccess_s**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalny nagłówek|
|-------------|---------------------|---------------------|
|**_access_s**|\<> io.h|\<> errno.h|
|**_waccess_s**|\<wchar.h> lub \<io.h>|\<> errno.h|

## <a name="example"></a>Przykład

W tym przykładzie użyto **_access_s,** aby sprawdzić plik o nazwie crt_access_s.c, aby sprawdzić, czy istnieje i czy zapis jest dozwolony.

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

## <a name="see-also"></a>Zobacz też

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
[_access, _waccess](access-waccess.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_stat, funkcje _wstat](stat-functions.md)
