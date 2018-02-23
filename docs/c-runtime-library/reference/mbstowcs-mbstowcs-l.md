---
title: "mbstowcs —, _mbstowcs_l — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- mbstowcs
- _mbstowcs_l
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- mbstowcs
dev_langs:
- C++
helpviewer_keywords:
- _mbstowcs_l function
- mbstowcs_l function
- mbstowcs function
ms.assetid: 96696b27-e068-4eeb-8006-3f7a0546ae6d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b422dbcb1d2fc07ff3fb1f00302b62da0500ebdc
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="mbstowcs-mbstowcsl"></a>mbstowcs, _mbstowcs_l
Konwertuje sekwencji znaków wielobajtowych sekwencji odpowiednie znaki dwubajtowe. Bezpieczniejsza wersje te funkcje są dostępne; zobacz [mbstowcs_s —, _mbstowcs_s_l —](../../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
size_t mbstowcs(  
   wchar_t *wcstr,  
   const char *mbstr,  
   size_t count   
);  
size_t _mbstowcs_l(  
   wchar_t *wcstr,  
   const char *mbstr,  
   size_t count,  
   _locale_t locale  
);  
template <size_t size>  
size_t mbstowcs(  
   wchar_t (&wcstr)[size],  
   const char *mbstr,  
   size_t count   
); // C++ only  
template <size_t size>  
size_t _mbstowcs_l(  
   wchar_t (&wcstr)[size],  
   const char *mbstr,  
   size_t count,  
   _locale_t locale  
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 [out] `wcstr`  
 Adres sekwencję znaki dwubajtowe.  
  
 [in] `mbstr`  
 Adres sekwencji null zakończone znaki wielobajtowe.  
  
 [in] `count`  
 Maksymalna liczba znaków wielobajtowych do konwersji.  
  
 [in] `locale`  
 Ustawienia regionalne do użycia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli `mbstowcs` pomyślnie konwertuje ciąg źródłowy zwraca liczbę znaków wielobajtowych przekonwertowany. Jeśli `wcstr` argument jest `NULL`, funkcja zwraca wymagany rozmiar (w znaki dwubajtowe) w ciągu docelowego. Jeśli `mbstowcs` napotkał nieprawidłowy znaków wielobajtowych, zwraca -1. Jeśli wartość zwracana jest `count`, ciąg znaków dwubajtowych nie jest zerem.  
  
> [!IMPORTANT]
>  Upewnij się, że `wcstr` i `mbstr` nie pokrywają oraz że `count` poprawnie odzwierciedla liczbę znaków wielobajtowych do konwersji.  
  
## <a name="remarks"></a>Uwagi  
 `mbstowcs` Funkcja konwertuje do maksymalnej liczby `count` znaków wielobajtowych wskazywana przez `mbstr` na ciąg odpowiednie znaki dwubajtowe, które zależą od bieżących ustawień regionalnych. Przechowuje wynikowy ciąg znaków dwubajtowych pod adresem reprezentowany przez `wcstr`. Wynik jest podobny do serii wywołań `mbtowc`. Jeśli `mbstowcs` napotka jednobajtowe znak null ('\0'), przed lub po `count` występuje konwertuje znak null znak null znaków dwubajtowych (L '\0') i kończy działanie. W związku z tym ciąg znaków dwubajtowych w `wcstr` jest zakończony wartością null tylko wtedy, gdy znak null napotkano podczas konwersji. Jeśli sekwencje wskazywana przez `wcstr` i `mbstr` nakładają się na siebie, zachowanie jest niezdefiniowany.  
  
 Jeśli `wcstr` argument jest `NULL`, `mbstowcs` zwraca liczbę znaki dwubajtowe, które byłyby wynikiem konwersji nie włącznie z terminatorem null. Ciąg źródłowy musi być zakończony zerem uzyskać prawidłową wartość zwracaną. Wynikowy ciąg znaków typu wide być zakończony zerem, należy dodać je do zwracanej wartości.  
  
 Jeśli `mbstr` argument jest `NULL`, lub jeśli `count` jest > `INT_MAX`, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md) . Jeśli wykonanie może kontynuować, numer błędu jest ustawiony na `EINVAL` i funkcja zwraca wartość -1.  
  
 `mbstowcs` używa bieżące ustawienia regionalne dla dowolnego zachowań zależnych od ustawień regionalnych. `_mbstowcs_l` jest identyczny z tą różnicą, że używa ustawień regionalnych przekazano zamiast tego. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).  
  
 W języku C++ te funkcje mają przeciążenia szablonu, które wywołują odpowiedników nowsza, bezpieczne tych funkcji. Aby uzyskać więcej informacji, zobacz [Secure szablonu Overloads](../../c-runtime-library/secure-template-overloads.md).  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`mbstowcs`|\<stdlib.h>|  
|`_mbstowcs_l`|\<stdlib.h>|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
  
```  
// crt_mbstowcs.c  
// compile with: /W3  
// illustrates the behavior of the mbstowcs function  
  
#include <stdlib.h>  
#include <stdio.h>  
#include <locale.h>  
  
int main( void )  
{  
    size_t size;  
    int nChar = 2; // number of characters to convert  
    int requiredSize;  
  
    unsigned char    *pmbnull  = NULL;  
    unsigned char    *pmbhello = NULL;  
    char* localeInfo;  
  
    wchar_t *pwchello = L"\x3042\x3043"; // 2 Hiragana characters  
    wchar_t *pwc;  
  
    /* Enable the Japanese locale and codepage */  
    localeInfo = setlocale(LC_ALL, "Japanese_Japan.932");  
    printf("Locale information set to %s\n", localeInfo);  
  
    printf( "Convert to multibyte string:\n" );  
  
    requiredSize = wcstombs( NULL, pwchello, 0); // C4996  
    // Note: wcstombs is deprecated; consider using wcstombs_s  
    printf("  Required Size: %d\n", requiredSize);  
  
    /* Add one to leave room for the null terminator. */  
    pmbhello = (unsigned char *)malloc( requiredSize + 1);  
    if (! pmbhello)  
    {  
        printf("Memory allocation failure.\n");  
        return 1;  
    }  
    size = wcstombs( pmbhello, pwchello, requiredSize + 1); // C4996  
    // Note: wcstombs is deprecated; consider using wcstombs_s  
    if (size == (size_t) (-1))  
    {  
        printf("Couldn't convert string. Code page 932 may"  
                " not be available.\n");  
        return 1;  
    }  
    printf( "  Number of bytes written to multibyte string: %u\n",  
            (unsigned int) size );  
    printf( "  Hex values of the " );  
    printf( " multibyte characters: %#.2x %#.2x %#.2x %#.2x\n",  
            pmbhello[0], pmbhello[1], pmbhello[2], pmbhello[3] );  
    printf( "  Codepage 932 uses 0x81 to 0x9f as lead bytes.\n\n");  
  
    printf( "Convert back to wide-character string:\n" );  
  
    /* Assume we don't know the length of the multibyte string.  
     Get the required size in characters, and allocate enough space. */  
  
    requiredSize = mbstowcs(NULL, pmbhello, 0); // C4996  
    /* Add one to leave room for the NULL terminator */  
    pwc = (wchar_t *)malloc( (requiredSize + 1) * sizeof( wchar_t ));  
    if (! pwc)  
    {  
        printf("Memory allocation failure.\n");  
        return 1;  
    }  
    size = mbstowcs( pwc, pmbhello, requiredSize + 1); // C4996  
    if (size == (size_t) (-1))  
    {  
       printf("Couldn't convert string--invalid multibyte character.\n");  
    }  
    printf( "  Characters converted: %u\n", (unsigned int)size );  
    printf( "  Hex value of first 2" );  
    printf( " wide characters: %#.4x %#.4x\n\n", pwc[0], pwc[1] );  
    free(pwc);  
    free(pmbhello);  
}  
```  
  
```Output  
Locale information set to Japanese_Japan.932  
Convert to multibyte string:  
  Required Size: 4  
  Number of bytes written to multibyte string: 4  
  Hex values of the  multibyte characters: 0x82 0xa0 0x82 0xa1  
  Codepage 932 uses 0x81 to 0x9f as lead bytes.  
  
Convert back to wide-character string:  
  Characters converted: 2  
  Hex value of first 2 wide characters: 0x3042 0x3043  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Konwersja danych](../../c-runtime-library/data-conversion.md)   
 [Ustawienia regionalne](../../c-runtime-library/locale.md)   
 [Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [_mbclen, mblen, _mblen_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)   
 [mbtowc, _mbtowc_l](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
 [wcstombs —, _wcstombs_l —](../../c-runtime-library/reference/wcstombs-wcstombs-l.md)   
 [wctomb —, _wctomb_l —](../../c-runtime-library/reference/wctomb-wctomb-l.md)   
 [MultiByteToWideChar](http://msdn.microsoft.com/library/windows/desktop/dd319072)