---
title: _strncnt, _wcsncnt, _mbsnbcnt, _mbsnbcnt_l, _mbsnccnt, _mbsnccnt_l | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _mbsnbcnt_l
- _mbsnccnt
- _wcsncnt
- _strncnt
- _mbsnccnt_l
- _mbsnbcnt
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
- _mbsnbcnt
- wcsncnt
- _tcsnbcnt
- _mbsnccnt
- _ftcsnbcnt
- mbsnbcnt
- strncnt
- mbsnbcnt_l
- mbsnccnt_l
- mbsnccnt
- _strncnt
- _wcsncnt
dev_langs: C++
helpviewer_keywords:
- _strncnt function
- _mbsnbcnt function
- _mbsnbcnt_l function
- _mbsnccnt_l function
- mbsnbcnt_l function
- mbsnbcnt function
- tcsnbcnt function
- mbsnccnt_l function
- strncnt function
- _tcsnbcnt function
- mbsnccnt function
- wcsncnt function
- _mbsnccnt function
- _wcsncnt function
ms.assetid: 2a022e9e-a307-4acb-a66b-e56e5357f848
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: cb2434cf25e6746637c13cdf8df7725555e839c9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="strncnt-wcsncnt-mbsnbcnt-mbsnbcntl-mbsnccnt-mbsnccntl"></a>_strncnt, _wcsncnt, _mbsnbcnt, _mbsnbcnt_l, _mbsnccnt, _mbsnccnt_l
Zwraca liczbę znaków lub bajtów w ciągu określonej liczby.  
  
> [!IMPORTANT]
>  `_mbsnbcnt`, `_mbsnbcnt_l`, `_mbsnccnt`, i `_mbsnccnt_l` nie można używać w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane z parametrem /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Składnia  
  
```  
size_t _strncnt(  
   const char *str,  
   size_t count  
);  
size_t _wcsncnt(  
   const wchar_t *str,  
   size_t count  
);  
size_t _mbsnbcnt(  
   const unsigned char *str,  
   size_t count   
);  
size_t _mbsnbcnt_l(  
   const unsigned char *str,  
   size_t count,  
   _locale_t locale  
);  
size_t _mbsnccnt(  
   const unsigned char *str,  
   size_t count  
);  
size_t _mbsnccnt_l(  
   const unsigned char *str,  
   size_t count,  
   _locale_t locale  
);  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `str`  
 Ciąg, który należy zbadać.  
  
 `count`  
 Liczba znaków lub bajtów do badania w `str`.  
  
 `locale`  
 Ustawienia regionalne do użycia.  
  
## <a name="return-value"></a>Wartość zwracana  
 `_mbsnbcnt`i `_mbsnbcnt_l` zwraca liczbę bajtów znaleziono w pierwszym `count` znaków wielobajtowych `str`. `_mbsnccnt`i `_mbsnccnt_l` zwraca liczbę znaków znaleziono w pierwszym `count` bajtów `str`. Jeśli przed analizy napotkano znak NULL `str` ma ukończone, zwróć liczbę bajtów lub znaków znaleziono przed znakiem NULL. Jeśli `str` składa się z mniej niż `count` znaków lub bajtów zwracają liczba znaków lub bajtów w ciągu. Jeśli `count` jest mniejsza od zera, zwracają 0. W poprzednich wersjach, funkcje te były zwracanej wartości typu `int` zamiast `size_t`.  
  
 `_strncnt`Zwraca liczbę znaków w pierwszym `count` bajtów ciągu jednobajtowe `str`. `_wcsncnt`Zwraca liczbę znaków w pierwszym `count` znaki dwubajtowe ciągu znaków dwubajtowych `str`.  
  
## <a name="remarks"></a>Uwagi  
 `_mbsnbcnt`i `_mbsnbcnt_l` liczbę bajtów znaleziono w pierwszym `count` znaków wielobajtowych `str`. `_mbsnbcnt`i `_mbsnbcnt_l` Zastąp `mtob` i powinna być używana zamiast `mtob`.  
  
 `_mbsnccnt`i `_mbsnccnt_l` liczbę znaleziono znaki w pierwszym `count` bajtów `str`. Jeśli `_mbsnccnt` i `_mbsnccnt_l` napotkasz wartość NULL w drugim bajtem znaków dwubajtowych, pierwszego bajtu również jest traktowany jako wartość NULL, a nie jest uwzględniony w liczba zwracanych wartości. `_mbsnccnt`i `_mbsnccnt_l` Zastąp `btom` i powinna być używana zamiast `btom`.  
  
 Jeśli `str` jest wskaźnika o wartości null lub jest `count` ma wartość 0, te funkcje Wywołaj program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md), `errno` ma ustawioną wartość `EINVAL`, a funkcja zwraca wartość 0.  
  
 Wartość wyjściowa jest zagrożony ustawienie `LC_CTYPE` ustawienie kategorii ustawień regionalnych; zobacz [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) Aby uzyskać więcej informacji. Wersje tych funkcji bez `_l` Użyj sufiksu bieżące ustawienia regionalne tego zachowania zależnych od ustawień regionalnych; wersje z `_l` sufiks są identyczne, z wyjątkiem tego, aby były używane zamiast przekazany parametr ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|-------------|--------------------------------------|--------------------|-----------------------|  
|`_tcsnbcnt`|`_strncnt`|`_mbsnbcnt`|`_wcsncnt`|  
|`_tcsnccnt`|`_strncnt`|`_mbsnbcnt`|`n/a`|  
|`_wcsncnt`|`n/a`|`n/a`|`_mbsnbcnt`|  
|`_wcsncnt`|`n/a`|`n/a`|`_mbsnccnt`|  
|`n/a`|`n/a`|`_mbsnbcnt_l`|`_mbsnccnt_l`|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_mbsnbcnt`|\<mbstring.h >|  
|`_mbsnbcnt_l`|\<mbstring.h >|  
|`_mbsnccnt`|\<mbstring.h >|  
|`_mbsnccnt_l`|\<mbstring.h >|  
|`_strncnt`|\<tchar.h >|  
|`_wcsncnt`|\<tchar.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Przykład  
  
```  
// crt_mbsnbcnt.c  
  
#include  <mbstring.h>  
#include  <stdio.h>  
  
int main( void )  
{  
   unsigned char str[] = "This is a multibyte-character string.";  
   unsigned int char_count, byte_count;  
   char_count = _mbsnccnt( str, 10 );  
   byte_count = _mbsnbcnt( str, 10 );  
   if ( byte_count - char_count )  
      printf( "The first 10 characters contain %d multibyte characters\n", char_count );  
   else  
      printf( "The first 10 characters are single-byte.\n");  
}  
```  
  
## <a name="output"></a>Dane wyjściowe  
  
```  
The first 10 characters are single-byte.  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)   
 [Ustawienia regionalne](../../c-runtime-library/locale.md)   
 [Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [_mbsnbcat —, _mbsnbcat_l —](../../c-runtime-library/reference/mbsnbcat-mbsnbcat-l.md)