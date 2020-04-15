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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 98726726e14aacec75ed99adfa33016b40affd17
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350871"
---
# <a name="_access-_waccess"></a>_access, _waccess

Określa, czy plik jest tylko do odczytu, czy nie. Dostępne są bezpieczniejsze wersje; patrz [_access_s, _waccess_s](access-s-waccess-s.md).

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

*Ścieżka*<br/>
Ścieżka pliku lub katalogu.

*Tryb*<br/>
Atrybut odczytu/zapisu.

## <a name="return-value"></a>Wartość zwracana

Każda funkcja zwraca wartość 0, jeśli plik ma dany tryb. Funkcja zwraca wartość -1, jeśli nazwany plik nie istnieje lub nie ma danego trybu; w tym `errno` przypadku jest ustawiona w sposób pokazany w poniższej tabeli.

|||
|-|-|
`EACCES`|Odmowa dostępu: ustawienie uprawnień pliku nie zezwala na określony dostęp.
`ENOENT`|Nie znaleziono nazwy pliku lub ścieżki.
`EINVAL`|Nieprawidłowy parametr.

Aby uzyskać więcej informacji na temat tych i innych kodów zwrotnych, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

W przypadku użycia z plikami funkcja **_access** określa, czy określony plik lub katalog istnieje i ma atrybuty określone przez wartość *trybu*. W przypadku użycia z katalogami **_access** określa tylko, czy określony katalog istnieje; w systemach operacyjnych Windows 2000 i nowszych katalogi mają dostęp do odczytu i zapisu.

|wartość *trybu*|Sprawdza plik dla|
|------------------|---------------------|
|00|Istnienie tylko|
|02|Tylko do zapisu|
|04|Tylko odczyt|
|06|Czytanie i pisanie|

Ta funkcja sprawdza tylko, czy plik i katalog są tylko do odczytu, czy nie, nie sprawdza ustawień zabezpieczeń systemu plików. Do tego potrzebny jest token dostępu. Aby uzyskać więcej informacji na temat zabezpieczeń systemu plików, zobacz [Tokeny dostępu](/windows/win32/SecAuthZ/access-tokens). Klasa ATL istnieje w celu zapewnienia tej funkcji; zobacz [CAccessToken Class](../../atl/reference/caccesstoken-class.md).

**_waccess** jest szerokoznakową wersją **_access;** argument *path* do **_waccess** jest ciągiem znaków o szerokim charakterze. **_waccess** i **_access** zachowują się identycznie w przeciwnym razie.

Ta funkcja sprawdza poprawność jego parametrów. Jeśli *ścieżka* ma wartość NULL lub *tryb* nie określa prawidłowego trybu, wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w obszarze Sprawdzanie [poprawności parametrów.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, funkcja `errno` ustawia `EINVAL` i zwraca -1.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|`_taccess`|**_access**|**_access**|**_waccess**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|----------------------|
|**_access**|\<> io.h|\<> errno.h|
|**_waccess**|\<wchar.h> lub \<io.h>|\<> errno.h|

## <a name="example"></a>Przykład

W poniższym przykładzie użyto **_access** do sprawdzenia pliku o nazwie crt_ACCESS. C, aby sprawdzić, czy istnieje i czy pisanie jest dozwolone.

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
