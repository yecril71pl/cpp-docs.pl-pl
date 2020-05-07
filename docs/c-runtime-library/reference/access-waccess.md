---
title: _access, _waccess
ms.date: 4/2/2020
api_name:
- _access
- _waccess
- _o__access
- _o__waccess
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _waccess
- _access
- taccess
- waccess
- _taccess
helpviewer_keywords:
- access function
- _taccess function
- waccess function
- _access function
- _waccess function
- taccess function
ms.assetid: ba34f745-85c3-49e5-a7d4-3590bd249dd3
ms.openlocfilehash: ae213768e30fa8120a80aaa30b3fe1b53e802d78
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920267"
---
# <a name="_access-_waccess"></a>_access, _waccess

Określa, czy plik jest tylko do odczytu, czy nie. Dostępne są bardziej bezpieczne wersje; Zobacz [_access_s, _waccess_s](access-s-waccess-s.md).

## <a name="syntax"></a>Składnia

```C
int _access(
   const char *path,
   int mode
);
int _waccess(
   const wchar_t *path,
   int mode
);
```

### <a name="parameters"></a>Parametry

*ścieżka*<br/>
Ścieżka pliku lub katalogu.

*wyst*<br/>
Atrybut odczytu/zapisu.

## <a name="return-value"></a>Wartość zwracana

Każda funkcja zwraca wartość 0, jeśli plik ma określony tryb. Funkcja zwraca wartość-1, jeśli nazwany plik nie istnieje lub nie ma podanego trybu; w tym przypadku jest `errno` ustawiony tak, jak pokazano w poniższej tabeli.

|||
|-|-|
`EACCES`|Odmowa dostępu: ustawienie uprawnienia pliku nie zezwala na określony dostęp.
`ENOENT`|Nie odnaleziono nazwy pliku lub ścieżki.
`EINVAL`|Nieprawidłowy parametr.

Aby uzyskać więcej informacji na temat tych i innych kodów powrotnych, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Gdy jest używany z plikami, funkcja **_access** określa, czy określony plik lub katalog istnieje i ma atrybuty określone przez wartość *trybu*. Gdy jest używany z katalogami, **_access** określa, czy określony katalog istnieje; w systemach operacyjnych Windows 2000 i nowszych wszystkie katalogi mają dostęp do odczytu i zapisu.

|wartość *trybu*|Sprawdza plik dla|
|------------------|---------------------|
|00|Tylko istnienie|
|02|Tylko do zapisu|
|04|Tylko odczyt|
|06|Odczyt i zapis|

Ta funkcja sprawdza tylko, czy plik i katalog są tylko do odczytu, czy nie, nie sprawdza ustawień zabezpieczeń systemu plików. Dla tego wymaga tokenu dostępu. Aby uzyskać więcej informacji na temat zabezpieczeń systemu plików, zobacz [tokeny dostępu](/windows/win32/SecAuthZ/access-tokens). Klasa ATL istnieje, aby zapewnić tę funkcję; Zobacz [Klasa CAccessToken](../../atl/reference/caccesstoken-class.md).

**_waccess** to dwubajtowa wersja **_access**; argument *ścieżki* **_waccess** jest ciągiem znaków dwubajtowych. **_waccess** i **_access** zachowują się identycznie w inny sposób.

Ta funkcja sprawdza poprawność swoich parametrów. Jeśli *ścieżka* ma wartość null lub w *trybie* nie określono prawidłowego trybu, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja ustawia `errno` jako `EINVAL` i zwraca wartość-1.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|`_taccess`|**_access**|**_access**|**_waccess**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|----------------------|
|**_access**|\<IO. h>|\<errno. h>|
|**_waccess**|\<WCHAR. h> lub \<IO. h>|\<errno. h>|

## <a name="example"></a>Przykład

Poniższy przykład używa **_access** do sprawdzenia pliku o nazwie crt_ACCESS. C, aby sprawdzić, czy istnieje, i czy zapis jest dozwolony.

```C
// crt_access.c
// compile with: /W1
// This example uses _access to check the file named
// crt_ACCESS.C to see if it exists and if writing is allowed.

#include  <io.h>
#include  <stdio.h>
#include  <stdlib.h>

int main( void )
{
    // Check for existence.
    if( (_access( "crt_ACCESS.C", 0 )) != -1 )
    {
        printf_s( "File crt_ACCESS.C exists.\n" );

        // Check for write permission.
        // Assume file is read-only.
        if( (_access( "crt_ACCESS.C", 2 )) == -1 )
            printf_s( "File crt_ACCESS.C does not have write permission.\n" );
    }
}
```

```Output
File crt_ACCESS.C exists.
File crt_ACCESS.C does not have write permission.
```

## <a name="see-also"></a>Zobacz też

[Obsługa plików](../../c-runtime-library/file-handling.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_stat, funkcje _wstat](stat-functions.md)
