---
title: "memmove_s —, wmemmove_s — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- wmemmove_s
- memmove_s
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- wmemmove_s
- memmove_s
dev_langs: C++
helpviewer_keywords:
- wmemmove_s function
- memmove_s function
ms.assetid: a17619e4-1307-4bb0-98c6-77f8c68dab2d
caps.latest.revision: "26"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 834cd18283874bc975d896f319bb6f8ebf962792
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="memmoves-wmemmoves"></a>memmove_s, wmemmove_s
Przenosi buforu na inny. Są to wersje [memmove —, wmemmove —](../../c-runtime-library/reference/memmove-wmemmove.md) ulepszeń zabezpieczeń zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      errno_t memmove_s(  
   void *dest,  
   size_t numberOfElements,  
   const void *src,  
   size_t count  
);  
errno_t wmemmove_s(  
   wchar_t *dest,  
   size_t numberOfElements,  
   const wchar_t *src,  
   size_t count  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dest`  
 Obiekt docelowy.  
  
 `numberOfElements`  
 Rozmiar buforu docelowego.  
  
 `src`  
 Obiekt źródłowy.  
  
 `count`  
 Liczba bajtów (`memmove_s`) ani znaków (`wmemmove_s`) do skopiowania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zero w przypadku powodzenia; Kod błędu w przypadku awarii  
  
### <a name="error-conditions"></a>Warunki błędów  
  
|`dest`|`numberOfElements`|`src`|Wartość zwracana|Zawartość`dest`|  
|------------|------------------------|-----------|------------------|------------------------|  
|`NULL`|wszystkie|wszystkie|`EINVAL`|Nie zmodyfikowano|  
|wszystkie|wszystkie|`NULL`|`EINVAL`|Nie zmodyfikowano|  
|wszystkie|< `count`|wszystkie|`ERANGE`|Nie zmodyfikowano|  
  
## <a name="remarks"></a>Uwagi  
 Kopie `count` bajtów znaków z `src` do `dest`. Jeśli nakładają się pewnych regionach obszar źródłowy i docelowy, `memmove_s` gwarantuje, że oryginalne źródło bajty nakładających się są kopiowane przed zastąpieniem.  
  
 Jeśli `dest` lub, jeśli `src` jest wskaźnika o wartości null, lub jeśli ciągu docelowego jest zbyt mały, te funkcje wywołanie program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md) . Jeśli jest dozwolone wykonywanie, aby kontynuować, te funkcje zwracają `EINVAL` i ustaw `errno` do `EINVAL`.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`memmove_s`|\<String.h >|  
|`wmemmove_s`|\<WChar.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
  
```  
// crt_memmove_s.c  
//  
// The program demonstrates the   
// memmove_s function which works as expected  
// for moving overlapping regions.  
  
#include <stdio.h>  
#include <string.h>  
  
int main()  
{  
   char str[] = "0123456789";  
  
   printf("Before: %s\n", str);  
  
   // Move six bytes from the start of the string  
   // to a new position shifted by one byte. To protect against  
   // buffer overrun, the secure version of memmove requires the  
   // the length of the destination string to be specified.   
  
   memmove_s((str + 1), strnlen(str + 1, 10), str, 6);   
  
   printf_s(" After: %s\n", str);  
}  
```  
  
## <a name="output"></a>Dane wyjściowe  
  
```  
Before: 0123456789  
 After: 0012345789  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Manipulowanie buforem](../../c-runtime-library/buffer-manipulation.md)   
 [_memccpy —](../../c-runtime-library/reference/memccpy.md)   
 [memcpy, wmemcpy —](../../c-runtime-library/reference/memcpy-wmemcpy.md)   
 [strcpy_s —, wcscpy_s —, _mbscpy_s —](../../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md)   
 [strcpy wcscpy —, _mbscpy —](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)   
 [strncpy_s — _strncpy_s_l —, wcsncpy_s —, _wcsncpy_s_l —, _mbsncpy_s, _mbsncpy_s_l](../../c-runtime-library/reference/strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)   
 [strncpy —, _strncpy_l —, wcsncpy —, _wcsncpy_l — _mbsncpy —, _mbsncpy_l —](../../c-runtime-library/reference/strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)