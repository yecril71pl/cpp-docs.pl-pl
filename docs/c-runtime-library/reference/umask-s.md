---
title: "_umask_s — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _umask_s
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
- unmask_s
- _umask_s
dev_langs: C++
helpviewer_keywords:
- masks, file-permission-setting
- _umask_s function
- masks
- file permissions [C++]
- umask_s function
- files [C++], permission settings for
ms.assetid: 70898f61-bf2b-4d8d-8291-0ccaa6d33145
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 67899d1dd082ffd023ca78ac8a4961288ffd0165
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="umasks"></a>_umask_s
Ustawia domyślną maskę uprawnień do pliku. Wersja [_umask —](../../c-runtime-library/reference/umask.md) ulepszeń zabezpieczeń zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
errno_t _umask_s(  
   int mode,  
   int * pOldMode  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in]`mode`  
 Domyślne ustawienie uprawnień.  
  
 [out]`oldMode`  
 Poprzedniej wartości ustawienia uprawnień.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca kod błędu, jeśli `Mode` nie określa prawidłowego trybu lub `pOldMode` wskaźnika jest `NULL`.  
  
### <a name="error-conditions"></a>Warunki błędów  
  
|`mode`|`pOldMode`|**Wartość zwracana**|**Zawartość**  `oldMode`|  
|------------|----------------|----------------------|--------------------------------|  
|wszystkie|`NULL`|`EINVAL`|Nie zmodyfikowano|  
|Nieprawidłowy tryb|wszystkie|`EINVAL`|Nie zmodyfikowano|  
  
 Jeśli wystąpi jedno z powyższych warunków, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, `_umask_s` zwraca `EINVAL` i ustawia `errno` do `EINVAL`.  
  
## <a name="remarks"></a>Uwagi  
 `_umask_s` Funkcja ustawia maski uprawnienia pliku bieżącego procesu do trybu określonego przez `mode`. Maska uprawnienia pliku Modyfikuje ustawienia uprawnień nowych plików utworzonych przez `_creat`, `_open`, lub `_sopen`. Jeśli bit maski to 1, odpowiadający mu bit pliku żądane uprawnienie wartość jest równa 0 (niedopuszczalne). Jeśli bit maski to 0, odpowiadający mu bit pozostanie bez zmian. Ustawienie uprawnień dla nowego pliku nie jest ustawiona, dopóki ten plik będzie zamknięty po raz pierwszy.  
  
 Wyrażenie całkowite `pmode` zawiera co najmniej jednej z następujących stałych manifestu, zdefiniowane w SYS\STAT. H:  
  
 `_S_IWRITE`  
 Zapisywanie dozwolone.  
  
 `_S_IREAD`  
 Odczytywanie dozwolone.  
  
 `_S_IREAD | _S_IWRITE`  
 Odczytywanie i zapisywanie dozwolone.  
  
 Gdy zarówno stałe są podane, są połączone z operator Alternatywy ( `|` ). Jeśli `mode` argument jest `_S_IREAD`, odczytu jest niedozwolony (plik jest tylko do zapisu). Jeśli `mode` argument jest `_S_IWRITE`, zapis nie jest dozwolone. (plik jest tylko do odczytu). Na przykład jeśli ustawiono bit zapisu maski, nowe pliki będą tylko do odczytu. Pamiętaj, że wszystkie pliki z systemu MS-DOS i systemów operacyjnych Windows, jest do odczytu; nie jest możliwe nadaj uprawnienia tylko do zapisu. W związku z tym ustawienie odczytu bit z `_umask_s` nie ma wpływu na tryby pliku.  
  
 Jeśli `pmode` nie jest kombinacją jednego z manifestu stałe lub zawiera inny zestaw stałych, funkcja będzie ignorować te.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_umask_s`|\<IO.h > i \<sys/stat.h > i \<sys/types.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
  
```  
// crt_umask_s.c  
/* This program uses _umask_s to set  
 * the file-permission mask so that all future  
 * files will be created as read-only files.  
 * It also displays the old mask.  
 */  
  
#include <sys/stat.h>  
#include <sys/types.h>  
#include <io.h>  
#include <stdio.h>  
  
int main( void )  
{  
   int oldmask, err;  
  
   /* Create read-only files: */  
   err = _umask_s( _S_IWRITE, &oldmask );  
   if (err)  
   {  
      printf("Error setting the umask.\n");  
      exit(1);  
   }  
   printf( "Oldmask = 0x%.4x\n", oldmask );  
}  
```  
  
```Output  
Oldmask = 0x0000  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa plików](../../c-runtime-library/file-handling.md)   
 [We/Wy niskiego poziomu](../../c-runtime-library/low-level-i-o.md)   
 [_chmod —, _wchmod —](../../c-runtime-library/reference/chmod-wchmod.md)   
 [_creat —, _wcreat —](../../c-runtime-library/reference/creat-wcreat.md)   
 [_mkdir —, _wmkdir —](../../c-runtime-library/reference/mkdir-wmkdir.md)   
 [_otwórz, _wopen —](../../c-runtime-library/reference/open-wopen.md)   
 [_umask —](../../c-runtime-library/reference/umask.md)