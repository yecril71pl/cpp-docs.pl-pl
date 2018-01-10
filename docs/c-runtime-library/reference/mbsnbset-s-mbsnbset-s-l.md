---
title: "_mbsnbset_s —, _mbsnbset_s_l — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _mbsnbset_s_l
- _mbsnbset_s
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
- api-ms-win-crt-multibyte-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- mbsnbset_s
- _mbsnbset_s_l
- _mbsnbset_s
- mbsnbset_s_l
dev_langs: C++
helpviewer_keywords:
- tcsnset_s function
- mbsnbset_s function
- mbsnbset_s_l function
- _mbsnbset_s_l function
- _tcsnset_s_l function
- _mbsnbset_s function
- _tcsnset_s function
- tcsnset_s_l function
ms.assetid: 811f92c9-cc31-4bbd-8017-2d1bfc6fb96f
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: dbda0fd8e7a3957d072bcaa95e510903fb84cb5e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="mbsnbsets-mbsnbsetsl"></a>_mbsnbset_s, _mbsnbset_s_l
Ustawia pierwszy `n` bajtów ciąg znaków wielobajtowych określony znak. Te wersje programu [_mbsnbset —, _mbsnbset_l —](../../c-runtime-library/reference/mbsnbset-mbsnbset-l.md) zostały ulepszone zabezpieczenia, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
> [!IMPORTANT]
>  Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane z parametrem /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Składnia  
  
```  
errno_t _mbsnbset_s(  
   unsigned char *str,  
   size_t size,  
   unsigned int c,  
   size_t count   
);  
errno_t _mbsnbset_s_l(  
   unsigned char *str,  
   size_t size,  
   unsigned int c,  
   size_t count,  
   _locale_t locale  
);  
template <size_t size>  
errno_t _mbsnbset_s(  
   unsigned char (&str)[size],  
   unsigned int c,  
   size_t count   
); // C++ only  
template <size_t size>  
errno_t _mbsnbset_s_l(  
   unsigned char (&str)[size],  
   unsigned int c,  
   size_t count,  
   _locale_t locale  
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 `str`  
 Ciąg, który ma zostać zmienione.  
  
 `size`  
 Rozmiar buforu ciągu.  
  
 `c`  
 Ustawienie jednobajtowe lub znaków wielobajtowych.  
  
 `count`  
 Liczba bajtów do ustawienia.  
  
 `locale`  
 Ustawienia regionalne do użycia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zero w przypadku powodzenia; w przeciwnym razie kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 `_mbsnbset_s` i `_mbsnbset_s_l` funkcje ustawiać co najwyżej pierwszy `count` bajtów `str` do `c`. Jeśli `count` jest większa niż długość `str`, długość `str` jest używany zamiast `count`. Jeśli `c` jest znaków wielobajtowych i nie można ustawić wyłącznie do ostatniego bajtu, który jest określony przez `count`, ostatniego bajtu jest uzupełniana znakiem puste. `_mbsnbset_s`i `_mbsnbset_s_l` nie umieszczaj kończącym wartości null na końcu `str`.  
  
 `_mbsnbset_s`i `_mbsnbset_s_l` przypominać `_mbsnset`, z wyjątkiem tego, że ich wartość `count` bajtów zamiast `count` znaków `c`.  
  
 Jeśli `str` jest `NULL` lub `count` wynosi zero, ta funkcja generuje wyjątek nieprawidłowy parametr zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, `errno` ustawiono `EINVAL` i funkcja zwraca `NULL`. Ponadto jeśli `c` nie jest prawidłową znaków wielobajtowych `errno` ustawiono `EINVAL` i spacji zamiast niego jest używana.  
  
 Wartość wyjściowa jest zagrożony ustawienie `LC_CTYPE` ustawienie kategorii ustawień regionalnych; zobacz [setlocale, _wsetlocale —](../../c-runtime-library/reference/setlocale-wsetlocale.md) Aby uzyskać więcej informacji. `_mbsnbset_s` Wersja tej funkcji używa bieżące ustawienia regionalne tego zachowania zależnych od ustawień regionalnych; `_mbsnbset_s_l` wersji jest identyczny z tą różnicą, że parametr ustawień regionalnych, który jest przekazywany w zamian używa. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).  
  
 W języku C++ użycia tych funkcji zostało uproszczone dzięki przeciążenia szablonu; przeciążeń można automatycznie rozpoznać długość buforu i tym samym, eliminując konieczność określić argument rozmiar. Aby uzyskać więcej informacji, zobacz [Secure szablonu Overloads](../../c-runtime-library/secure-template-overloads.md).  
  
 Wersje tych funkcji do debugowania najpierw wprowadzić bufor 0xFD. Aby wyłączyć to zachowanie, użyj [_crtsetdebugfillthreshold —](../../c-runtime-library/reference/crtsetdebugfillthreshold.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tcsnset_s`|`_strnset_s`|`_mbsnbset_s`|`_wcsnset_s`|  
|`_tcsnset_s_l`|`_strnset_s _l`|`_mbsnbset_s_l`|`_wcsnset_s_l`|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_mbsnbset_s`|\<mbstring.h >|  
|`_mbsnbset_s_l`|\<mbstring.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Przykład  
  
```  
// crt_mbsnbset_s.c  
#include <mbstring.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char string[15] = "This is a test";  
   /* Set not more than 4 bytes of string to be *'s */  
   printf( "Before: %s\n", string );  
   _mbsnbset_s( string, sizeof(string), '*', 4 );  
   printf( "After:  %s\n", string );  
}  
```  
  
## <a name="output"></a>Dane wyjściowe  
  
```Output  
Before: This is a test  
After:  **** is a test  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)   
 [_mbsnbcat —, _mbsnbcat_l —](../../c-runtime-library/reference/mbsnbcat-mbsnbcat-l.md)   
 [_strnset —, _strnset_l —, _wcsnset —, _wcsnset_l — _mbsnset —, _mbsnset_l —](../../c-runtime-library/reference/strnset-strnset-l-wcsnset-wcsnset-l-mbsnset-mbsnset-l.md)   
 [_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](../../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)