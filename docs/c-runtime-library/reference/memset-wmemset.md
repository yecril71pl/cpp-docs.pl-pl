---
title: "memset —, wmemset — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- wmemset
- memset
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
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- memset
- wmemset
dev_langs: C++
helpviewer_keywords:
- wmemset function
- memset function
ms.assetid: e7ceb01b-df69-49c2-b294-a39358ad4699
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1b9f15d86f3ec64c0179f0401cd4deffa2e757ba
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="memset-wmemset"></a>memset, wmemset
Ustawia buforów określony znak.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      void *memset(  
   void *dest,  
   int c,  
   size_t count   
);  
wchar_t *wmemset(  
   wchar_t *dest,  
   wchar_t c,  
   size_t count  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 *docelowy*  
 Wskaźnik do miejsca docelowego.  
  
 `c`  
 Znak do ustawienia.  
  
 *Liczba*  
 Liczba znaków.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartość `dest`.  
  
## <a name="remarks"></a>Uwagi  
 Ustawia pierwszy `count` znaków `dest` na znak `c`.  
  
 **Uwaga dotycząca zabezpieczeń** upewnij się, że bufor docelowy ma za mało miejsca na co najmniej `count` znaków. Aby uzyskać więcej informacji, zobacz [unikanie Overruns buforu](http://msdn.microsoft.com/library/windows/desktop/ms717795).  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`memset`|\<Memory.h > lub \<string.h >|  
|`wmemset`|\<WChar.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="libraries"></a>Biblioteki  
 Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Przykład  
  
```  
// crt_memset.c  
/* This program uses memset to  
 * set the first four chars of buffer to "*".  
 */  
  
#include <memory.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char buffer[] = "This is a test of the memset function";  
  
   printf( "Before: %s\n", buffer );  
   memset( buffer, '*', 4 );  
   printf( "After:  %s\n", buffer );  
}  
```  
  
## <a name="output"></a>Dane wyjściowe  
  
```  
Before: This is a test of the memset function  
After:  **** is a test of the memset function  
```  
  
 Oto przykład wykorzystania wmemset —:  
  
```  
// crt_wmemset.c  
/* This program uses memset to  
 * set the first four chars of buffer to "*".  
 */  
  
#include <wchar.h>  
#include <stdio.h>  
  
int main( void )  
{  
   wchar_t buffer[] = L"This is a test of the wmemset function";  
  
   wprintf( L"Before: %s\n", buffer );  
   wmemset( buffer, '*', 4 );  
   wprintf( L"After:  %s\n", buffer );  
}  
```  
  
## <a name="output"></a>Dane wyjściowe  
  
```  
Before: This is a test of the wmemset function  
After:  **** is a test of the wmemset function  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Manipulowanie buforem](../../c-runtime-library/buffer-manipulation.md)   
 [_memccpy —](../../c-runtime-library/reference/memccpy.md)   
 [memchr, wmemchr —](../../c-runtime-library/reference/memchr-wmemchr.md)   
 [funkcji memcmp, wmemcmp —](../../c-runtime-library/reference/memcmp-wmemcmp.md)   
 [memcpy, wmemcpy —](../../c-runtime-library/reference/memcpy-wmemcpy.md)   
 [_strnset, _strnset_l, _wcsnset, _wcsnset_l, _mbsnset, _mbsnset_l](../../c-runtime-library/reference/strnset-strnset-l-wcsnset-wcsnset-l-mbsnset-mbsnset-l.md)