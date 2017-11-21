---
title: "_access —, _waccess — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
helpviewer_keywords:
- access function
- _taccess function
- waccess function
- _access function
- _waccess function
- taccess function
ms.assetid: ba34f745-85c3-49e5-a7d4-3590bd249dd3
caps.latest.revision: "27"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8523e2f2e0a3550c6b996fa26387b278b6df94ed
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="access-waccess"></a>_access, _waccess
Określa, czy plik jest tylko do odczytu lub nie. Bezpieczniejsza wersje są dostępne; zobacz [_access_s —, _waccess_s —](../../c-runtime-library/reference/access-s-waccess-s.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
int _access(   
   const char *path,   
   int mode   
);  
int _waccess(   
   const wchar_t *path,   
   int mode   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `path`  
 Ścieżka pliku lub katalogu.  
  
 `mode`  
 Atrybut odczytu/zapisu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Każda funkcja zwraca wartość 0, jeśli plik ma danej metody. Funkcja zwraca wartość -1, jeśli plik o nazwie nie istnieje lub nie ma podanego trybu; w takim przypadku `errno` jest ustawiona, jak pokazano w poniższej tabeli.  
  
 `EACCES`  
 Odmowa dostępu: ustawienie uprawnienia pliku zezwalają na dostęp określony.  
  
 `ENOENT`  
 Nazwa pliku lub nie można odnaleźć ścieżki.  
  
 `EINVAL`  
 Nieprawidłowy parametr.  
  
 Aby uzyskać więcej informacji na temat tych i innych kody powrotu, zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Uwagi  
 W przypadku użycia z plików, `_access` funkcji określa, czy określony plik lub katalog istnieje i ma atrybuty określone przez wartość `mode`. W przypadku użycia z katalogów, `_access` tylko określa, czy istnieje określony katalog; w [!INCLUDE[Win2kFamily](../../c-runtime-library/includes/win2kfamily_md.md)] i później w systemie operacyjnym, wszystkie katalogi ma uprawnienia odczytu i zapisu.  
  
|`mode`wartość|Sprawdzanie pliku|  
|------------------|---------------------|  
|00|Istnienie tylko|  
|02|Tylko do zapisu|  
|04|tylko do odczytu|  
|06|Odczyt i zapis|  
  
 Ta funkcja tylko sprawdza, czy plików i katalogów są tylko do odczytu lub nie, nie sprawdza ustawienia zabezpieczeń systemu plików. W tym należy tokenu dostępu. Aby uzyskać więcej informacji dotyczących zabezpieczeń systemu plików, zobacz [tokenów dostępu](http://msdn.microsoft.com/library/windows/desktop/aa374909). Klasy ATL istnieje w celu zapewnienia tej funkcji; zobacz [CAccessToken klasy](../../atl/reference/caccesstoken-class.md).  
  
 `_waccess`jest to wersja znaków dwubajtowych `_access`; `path` argument `_waccess` jest ciągiem znaków dwubajtowych. `_waccess`i `_access` zachowują się tak samo w przeciwnym razie wartość.  
  
 Ta funkcja weryfikuje jego parametrów. Jeśli `path` jest `NULL` lub `mode` nie określa prawidłowego trybu, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może kontynuować, funkcja ustawia `errno` do `EINVAL` i zwraca wartość -1.  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_taccess`|`_access`|`_access`|`_waccess`|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|  
|-------------|---------------------|----------------------|  
|`_access`|\<IO.h >|\<errno.h >|  
|`_waccess`|\<WChar.h > lub \<io.h >|\<errno.h >|  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `_access` sprawdzić plik o nazwie crt_ACCESS. C, aby sprawdzić, czy istnieje i czy jest dozwolone zapisu.  
  
```  
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
 [Obsługa plików](../../c-runtime-library/file-handling.md)   
 [_chmod —, _wchmod —](../../c-runtime-library/reference/chmod-wchmod.md)   
 [_fstat —, _fstat32 —, _fstat64 —, _fstati64 — _fstat32i64 —, _fstat64i32 —](../../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)   
 [_otwórz, _wopen —](../../c-runtime-library/reference/open-wopen.md)   
 [_stat, _wstat — funkcje](../../c-runtime-library/reference/stat-functions.md)