---
title: _access, _waccess — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _access
- _waccess
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
- _waccess
- _access
- taccess
- waccess
- _taccess
dev_langs:
- C++
helpviewer_keywords:
- access function
- _taccess function
- waccess function
- _access function
- _waccess function
- taccess function
ms.assetid: ba34f745-85c3-49e5-a7d4-3590bd249dd3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 77876aad65a06cd541949937898496f811375e58
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43209606"
---
# <a name="access-waccess"></a>_access, _waccess

Określa, czy plik jest tylko do odczytu, czy nie. Bardziej bezpieczne wersje są dostępne; zobacz [_access_s —, _waccess_s —](access-s-waccess-s.md).

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

*Ścieżka*  
Ścieżka pliku lub katalogu.

*Tryb*  
Atrybut odczytu/zapisu.

## <a name="return-value"></a>Wartość zwracana

Każda funkcja zwraca 0, jeśli plik ma w danym trybie. Funkcja zwraca wartość -1, jeśli plik o nazwie nie istnieje lub nie ma podanego trybu; w tym przypadku `errno` jest ustawiona, jak pokazano w poniższej tabeli.

|||
|-|-|
`EACCES`|Odmowa dostępu: ustawienie uprawnienia pliku zezwalają na dostęp określonym.
`ENOENT`|Nazwa pliku lub nie można odnaleźć ścieżki.
`EINVAL`|Nieprawidłowy parametr.

Aby uzyskać więcej informacji na temat tych i innych kodach powrotnych, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Gdy jest używana z plikami, **_access** funkcja określa, czy określony plik lub katalog istnieje i ma atrybuty określone przez wartość *tryb*. Gdy jest używana z katalogami, **_access** określa jedynie, czy podany katalog istnieje; w Windows 2000 i nowszych systemów operacyjnych, wszystkie katalogi ma uprawnienia odczytu i zapisu.

|*tryb* wartość|Plik kontroli|
|------------------|---------------------|
|00|Istnienie tylko|
|02|Tylko do zapisu|
|04|tylko do odczytu|
|06|Odczyt i zapis|

Ta funkcja sprawdza tylko, czy plików i katalogów są tylko do odczytu lub nie, nie sprawdza ustawienia zabezpieczeń systemu plików. W tym należy tokenu dostępu. Aby uzyskać więcej informacji na temat zabezpieczeń systemu plików, zobacz [tokenów dostępu](/windows/desktop/SecAuthZ/access-tokens). Klasy ATL istnieje w celu zapewnienia tej funkcji; zobacz [klasa CAccessToken](../../atl/reference/caccesstoken-class.md).

**_waccess —** to wersja znaku dwubajtowego **_access**; *ścieżki* argument **_waccess —** jest ciągiem znaku dwubajtowego. **_waccess —** i **_access** zachowują się identycznie.

Ta funkcja sprawdza poprawność swoich parametrów. Jeśli *ścieżki* ma wartość NULL lub *tryb* nie określa prawidłowego trybu wywołany nieprawidłowy parametr uchwytu, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, funkcja ustawia `errno` do `EINVAL` i zwraca wartość -1.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|`_taccess`|**_access**|**_access**|**_waccess**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|----------------------|
|**_access**|\<io.h>|\<errno.h>|
|**_waccess**|\<WChar.h > lub \<io.h >|\<errno.h>|

## <a name="example"></a>Przykład

W poniższym przykładzie użyto **_access** można znaleźć w pliku o nazwie crt_ACCESS. C, aby zobaczyć, czy istnieje i czy jest dozwolone zapisywanie.

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

## <a name="see-also"></a>Zobacz także

[Obsługa plików](../../c-runtime-library/file-handling.md)  
[_chmod, _wchmod](chmod-wchmod.md)  
[_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)  
[_open, _wopen](open-wopen.md)  
[_stat, _wstat — funkcje](stat-functions.md)  