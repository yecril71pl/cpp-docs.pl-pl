---
title: "_access_s —, _waccess_s — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
helpviewer_keywords:
- access_s function
- taccess_s function
- _taccess_s function
- waccess_s function
- _access_s function
- _waccess_s function
ms.assetid: fb3004fc-dcd3-4569-8b27-d817546e947e
caps.latest.revision: "28"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f562d62f3edb1f09fe6d7ebe7b509411ad2dc8c6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="accesss-waccesss"></a>_access_s, _waccess_s
Określa uprawnienia odczytu/zapisu do pliku. To jest wersja [_access —, _waccess —](../../c-runtime-library/reference/access-waccess.md) ulepszeń zabezpieczeń zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
errno_t _access_s(   
   const char *path,   
   int mode   
);  
errno_t _waccess_s(   
   const wchar_t *path,   
   int mode   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `path`  
 Ścieżka pliku lub katalogu.  
  
 `mode`  
 Ustawienie uprawnień.  
  
## <a name="return-value"></a>Wartość zwracana  
 Każda funkcja zwraca wartość 0, jeśli plik ma danej metody. Jeśli plik o nazwie nie istnieje lub nie jest dostępny w trybie danego, funkcja zwraca kod błędu. W takim przypadku funkcja zwraca kod błędu z zestawu w następujący sposób i ustawia również `errno` na tę samą wartość.  
  
 `EACCES`  
 Odmowa dostępu. Ustawienie uprawnień pliku nie zezwala na dostęp określonym.  
  
 `ENOENT`  
 Nazwa pliku lub nie można odnaleźć ścieżki.  
  
 `EINVAL`  
 Nieprawidłowy parametr.  
  
 Aby uzyskać więcej informacji, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Uwagi  
 W przypadku użycia z plików, `_access_s` funkcji określa, czy określony plik istnieje i jest dostępny jako określony przez wartość `mode`. W przypadku użycia z katalogów `_access_s` tylko określa, czy istnieje określony katalog. W [!INCLUDE[Win2kFamily](../../c-runtime-library/includes/win2kfamily_md.md)] i później w systemie operacyjnym, wszystkie katalogi ma uprawnienia odczytu i zapisu.  
  
|wartość trybu|Sprawdzanie pliku|  
|----------------|---------------------|  
|00|Istnienie tylko.|  
|02|Uprawnienie do zapisu.|  
|04|Uprawnienie do odczytu.|  
|06|Uprawnienia odczytu i zapisu.|  
  
 Uprawnienia do odczytu lub zapisu pliku nie jest wystarczająco, aby zapewnić możliwość otwarcia pliku. Na przykład, jeśli plik jest zablokowany przez inny proces, może nie być on dostępny nawet jeśli `_access_s` zwraca wartość 0.  
  
 `_waccess_s`jest to wersja znaków dwubajtowych `_access_s`, gdzie `path` argument `_waccess_s` jest ciągiem znaków dwubajtowych. W przeciwnym razie `_waccess_s` i `_access_s` zachowują się tak samo.  
  
 Te funkcje walidację ich parametrów. Jeśli `path` jest `NULL` lub `mode` nie określa prawidłowego trybu, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli dozwolone jest wykonywanie aby kontynuować, ustawianie tych funkcji `errno` do `EINVAL` i zwracać `EINVAL`.  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_taccess_s`|`_access_s`|`_access_s`|`_waccess_s`|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|  
|-------------|---------------------|---------------------|  
|`_access_s`|\<IO.h >|\<errno.h >|  
|`_waccess_s`|\<WChar.h > lub \<io.h >|\<errno.h >|  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `_access_s` sprawdzić plik o nazwie crt_access_s.c, aby sprawdzić, czy istnieje i czy jest dozwolone zapisu.  
  
```  
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
 [Obsługa plików](../../c-runtime-library/file-handling.md)   
 [_access —, _waccess —](../../c-runtime-library/reference/access-waccess.md)   
 [_chmod —, _wchmod —](../../c-runtime-library/reference/chmod-wchmod.md)   
 [_fstat —, _fstat32 —, _fstat64 —, _fstati64 — _fstat32i64 —, _fstat64i32 —](../../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)   
 [_otwórz, _wopen —](../../c-runtime-library/reference/open-wopen.md)   
 [_stat, _wstat — funkcje](../../c-runtime-library/reference/stat-functions.md)