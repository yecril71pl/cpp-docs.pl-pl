---
title: "_memicmp —, _memicmp_l — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _memicmp_l
- _memicmp
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
- _memicmp
- memicmp_l
- _memicmp_l
dev_langs: C++
helpviewer_keywords:
- memicmp function
- _memicmp function
- memicmp_l function
- _memicmp_l function
ms.assetid: 0a6eb945-4077-4f84-935d-1aaebe8db8cb
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: adfbab425e5765ce23522612c628b5b83da444b5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="memicmp-memicmpl"></a>_memicmp, _memicmp_l
Porównanie znaków w dwóch buforów (bez uwzględniania wielkości liter).  
  
## <a name="syntax"></a>Składnia  
  
```  
int _memicmp(  
   const void *buf1,  
   const void *buf2,  
   size_t count   
);  
int _memicmp_l(  
   const void *buf1,  
   const void *buf2,  
   size_t count,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `buf1`  
 Pierwszy buforu.  
  
 `buf2`  
 Drugi buforu.  
  
 `count`  
 Liczba znaków.  
  
 `locale`  
 Ustawienia regionalne do użycia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartości zwracanej wskazuje relację między buforów.  
  
|Wartość zwracana|Relacja pierwszych bajtów Liczba buf1 i buf2|  
|------------------|--------------------------------------------------------|  
|< 0|`buf1`mniej niż `buf2`.|  
|0|`buf1`taki sam jak `buf2`.|  
|> 0|`buf1`większa niż `buf2`.|  
|`_NLSCMPERROR`|Wystąpił błąd.|  
  
## <a name="remarks"></a>Uwagi  
 `_memicmp` Funkcja porównuje pierwszy `count` znaków dwóch buforów `buf1` i `buf2` po bicie. Porównanie nie jest rozróżniana wielkość liter.  
  
 Jeśli dowolny `buf1` lub `buf2` jest wskaźnika o wartości null, funkcja wywołuje program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, funkcja zwraca `_NLSCMPERROR` i ustawia `errno` do `EINVAL`.  
  
 `_memicmp`używa bieżące ustawienia regionalne dla zachowań zależnych od ustawień regionalnych. `_memicmp_l` jest identyczny z tą różnicą, że używa ustawień regionalnych przekazano zamiast tego. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_memicmp`|\<Memory.h > lub \<string.h >|  
|`_memicmp_l`|\<Memory.h > lub \<string.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
  
```  
// crt_memicmp.c  
// This program uses _memicmp to compare  
// the first 29 letters of the strings named first and  
// second without regard to the case of the letters.  
  
#include <memory.h>  
#include <stdio.h>  
#include <string.h>  
  
int main( void )  
{  
   int result;  
   char first[] = "Those Who Will Not Learn from History";  
   char second[] = "THOSE WHO WILL NOT LEARN FROM their mistakes";  
   // Note that the 29th character is right here ^  
  
   printf( "Compare '%.29s' to '%.29s'\n", first, second );  
   result = _memicmp( first, second, 29 );  
   if( result < 0 )  
      printf( "First is less than second.\n" );  
   else if( result == 0 )  
      printf( "First is equal to second.\n" );  
   else if( result > 0 )  
      printf( "First is greater than second.\n" );  
}  
```  
  
```Output  
Compare 'Those Who Will Not Learn from' to 'THOSE WHO WILL NOT LEARN FROM'  
First is equal to second.  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Manipulowanie buforem](../../c-runtime-library/buffer-manipulation.md)   
 [_memccpy —](../../c-runtime-library/reference/memccpy.md)   
 [memchr, wmemchr —](../../c-runtime-library/reference/memchr-wmemchr.md)   
 [funkcji memcmp, wmemcmp —](../../c-runtime-library/reference/memcmp-wmemcmp.md)   
 [memcpy, wmemcpy —](../../c-runtime-library/reference/memcpy-wmemcpy.md)   
 [memset —, wmemset —](../../c-runtime-library/reference/memset-wmemset.md)   
 [_stricmp —, _wcsicmp —, _mbsicmp —, _stricmp_l — _wcsicmp_l —, _mbsicmp_l —](../../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)   
 [_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)