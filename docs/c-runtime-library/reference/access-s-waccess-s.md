---
title: _access_s, _waccess_s
ms.date: 11/04/2016
api_name:
- _access_s
- _waccess_s
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
ms.openlocfilehash: e7e61369635a1a59ef16aa6262650d9648277eb0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171323"
---
# <a name="_access_s-_waccess_s"></a>_access_s, _waccess_s

Określa uprawnienia do odczytu/zapisu w pliku. Jest to wersja [_access, _waccess](access-waccess.md) z ulepszonymi zabezpieczeniami, zgodnie z opisem w temacie [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*path*<br/>
Ścieżka pliku lub katalogu.

*wyst*<br/>
Ustawienie uprawnień.

## <a name="return-value"></a>Wartość zwracana

Każda funkcja zwraca wartość 0, jeśli plik ma określony tryb. Funkcja zwraca kod błędu, jeśli nazwany plik nie istnieje lub jest niedostępny w danym trybie. W takim przypadku funkcja zwraca kod błędu z zestawu w następujący sposób, a także ustawia `errno` na tę samą wartość.

|errno wartość|Warunek|
|-|-|
`EACCES`|Odmowa dostępu. Ustawienie uprawnienia pliku nie zezwala na określony dostęp.
`ENOENT`|Nie odnaleziono nazwy pliku lub ścieżki.
`EINVAL`|Nieprawidłowy parametr.

Aby uzyskać więcej informacji, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

W przypadku użycia z plikami funkcja **_access_s** określa, czy określony plik istnieje i czy można uzyskać do niego dostęp zgodnie z określoną wartością *trybu*. W przypadku używania z katalogami, **_access_s** określa, czy istnieje określony katalog. W systemach operacyjnych Windows 2000 i nowszych wszystkie katalogi mają dostęp do odczytu i zapisu.

|wartość trybu|Sprawdza plik dla|
|----------------|---------------------|
|00|Tylko istnienie.|
|02|Uprawnienie do zapisu.|
|04|Uprawnienie Odczyt.|
|06|Uprawnienia do odczytu i zapisu.|

Uprawnienie do odczytu lub zapisu pliku jest za mało, aby można było otworzyć plik. Na przykład, jeśli plik jest zablokowany przez inny proces, może nie być dostępny, nawet jeśli **_access_s** zwraca 0.

**_waccess_s** to wersja znaku dwubajtowego **_access_s**, gdzie argument *ścieżki* **_waccess_s** jest ciągiem znaków dwubajtowych. W przeciwnym razie **_waccess_s** i **_access_s** zachowują się identycznie.

Te funkcje sprawdzają poprawność swoich parametrów. Jeśli *ścieżka* ma wartość null lub w *trybie* nie określono prawidłowego trybu, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje ustawiają `errno` na `EINVAL` i zwracają `EINVAL`.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|`_taccess_s`|**_access_s**|**_access_s**|**_waccess_s**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalny nagłówek|
|-------------|---------------------|---------------------|
|**_access_s**|\<we/wy >|\<errno. h >|
|**_waccess_s**|\<WCHAR. h > lub \<we/wy >|\<errno. h >|

## <a name="example"></a>Przykład

W tym przykładzie używa się **_access_s** do sprawdzenia pliku o nazwie crt_access_s. c, aby sprawdzić, czy istnieje, i czy zapis jest dozwolony.

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
