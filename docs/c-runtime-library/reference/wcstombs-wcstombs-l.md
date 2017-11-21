---
title: "wcstombs —, _wcstombs_l — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- wcstombs
- _wcstombs_l
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
- wcstombs
- _wcstombs_l
dev_langs: C++
helpviewer_keywords:
- _wcstombs_l function
- wcstombs function
- string conversion, wide characters
- wide characters, converting
- wcstombs_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 91234252-9ea1-423a-af99-e9d0ce4a40e3
caps.latest.revision: "30"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: fa142902722ac5df6ac93b28daf9e76b99f54f5e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="wcstombs-wcstombsl"></a>wcstombs, _wcstombs_l
Konwertuje odpowiedniej sekwencji znaków wielobajtowych sekwencji znaki dwubajtowe. Bezpieczniejsza wersje te funkcje są dostępne; zobacz [wcstombs_s —, _wcstombs_s_l —](../../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
size_t wcstombs(  
   char *mbstr,  
   const wchar_t *wcstr,  
   size_t count   
);  
size_t _wcstombs_l(  
   char *mbstr,  
   const wchar_t *wcstr,  
   size_t count,  
   _locale_t locale  
);  
template <size_t size>  
size_t wcstombs(  
   char (&mbstr)[size],  
   const wchar_t *wcstr,  
   size_t count   
); // C++ only  
template <size_t size>  
size_t _wcstombs_l(  
   char (&mbstr)[size],  
   const wchar_t *wcstr,  
   size_t count,  
   _locale_t locale  
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 `mbstr`  
 Adres sekwencji znaków wielobajtowych.  
  
 `wcstr`  
 Adres sekwencję znaki dwubajtowe.  
  
 `count`  
 Maksymalna liczba bajtów, które mogą być przechowywane w ciągu znaków wielobajtowych danych wyjściowych.  
  
 `locale`  
 Ustawienia regionalne do użycia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli `wcstombs` pomyślnie konwertuje ciąg znaków wielobajtowych, zwraca liczbę bajtów zapisanych w ciągu wielobajtowe dane wyjściowe, z wyłączeniem przerywanie `NULL` (jeśli istnieje). Jeśli `mbstr` argument jest `NULL`, `wcstombs` zwraca wymagany rozmiar w bajtach ciągu docelowego. Jeśli `wcstombs` napotka znaków dwubajtowych nie można przekonwertować znaków wielobajtowych, zwraca -1 rzutowany na typ `size_t` i ustawia `errno` do `EILSEQ`.  
  
## <a name="remarks"></a>Uwagi  
 `wcstombs` Funkcja konwertuje ciąg znaków dwubajtowych wskazywana przez `wcstr` do odpowiedniego wielobajtowych znaków i przechowuje wyniki w `mbstr` tablicy. `count` Parametr wskazuje maksymalną liczbę bajtów, które mogą być przechowywane w ciągu wyjściowego Wielobajtowe (to znaczy, że rozmiar `mbstr`). Ogólnie rzecz biorąc nie wiadomo, ile bajty będzie wymagane podczas konwertowania ciągu znaków dwubajtowych. Niektóre znaki dwubajtowe wymaga tylko jednego bajtu w ciągu wyjściowego; inne wymagają dwa. Jeśli istnieją dwa bajty w ciągu wielobajtowe danych wyjściowych dla każdego znaku dwubajtowego w ciągu wejściowym (w tym znaków dwubajtowych `NULL`), wynik jest gwarantowana w celu dopasowania.  
  
 Jeśli `wcstombs` napotka znak null znaków dwubajtowych (L '\0'), przed lub po `count` występuje i konwertuje ją na 8-bitowej 0 i powoduje zatrzymanie. W związku z tym ciąg znaków wielobajtowych `mbstr` jest zakończony wartością null tylko wtedy, gdy `wcstombs` napotka znak null znaków dwubajtowych podczas konwersji. Jeśli sekwencje wskazywana przez `wcstr` i `mbstr` nakładają się zachowanie `wcstombs` jest niezdefiniowana.  
  
 Jeśli `mbstr` argument jest `NULL`, `wcstombs` zwraca wymagany rozmiar w bajtach ciągu docelowego.  
  
 `wcstombs`sprawdza poprawność parametrów. Jeśli `wcstr` jest `NULL`, lub jeśli `count` jest większa niż `INT_MAX`, ta funkcja wywołuje program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md) . Jeśli wykonanie może kontynuować, funkcja ustawia `errno` do `EINVAL` i zwraca wartość -1.  
  
 `wcstombs`używa bieżące ustawienia regionalne dla dowolnego zachowań zależnych od ustawień regionalnych. `_wcstombs_l` jest identyczny z tą różnicą, że używa ustawień regionalnych przekazano zamiast tego. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).  
  
 W języku C++ te funkcje mają przeciążenia szablonu, które wywołują odpowiedników nowsza, bezpieczne tych funkcji. Aby uzyskać więcej informacji, zobacz [Secure szablonu Overloads](../../c-runtime-library/secure-template-overloads.md).  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`wcstombs`|\<stdlib.h >|  
|`_wcstombs_l`|\<stdlib.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.  
  
## <a name="example"></a>Przykład  
 Ten program ilustruje zachowanie `wcstombs` funkcji.  
  
```  
// crt_wcstombs.c  
// compile with: /W3  
// This example demonstrates the use  
// of wcstombs, which converts a string  
// of wide characters to a string of   
// multibyte characters.  
  
#include <stdlib.h>  
#include <stdio.h>  
  
#define BUFFER_SIZE 100  
  
int main( void )  
{  
    size_t  count;  
    char    *pMBBuffer = (char *)malloc( BUFFER_SIZE );  
    wchar_t *pWCBuffer = L"Hello, world.";  
  
    printf("Convert wide-character string:\n" );  
  
    count = wcstombs(pMBBuffer, pWCBuffer, BUFFER_SIZE ); // C4996  
    // Note: wcstombs is deprecated; consider using wcstombs_s instead  
    printf("   Characters converted: %u\n",  
            count );  
    printf("    Multibyte character: %s\n\n",  
           pMBBuffer );  
  
    free(pMBBuffer);  
}  
```  
  
```Output  
Convert wide-character string:  
   Characters converted: 13  
    Multibyte character: Hello, world.  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Konwersja danych](../../c-runtime-library/data-conversion.md)   
 [Ustawienia regionalne](../../c-runtime-library/locale.md)   
 [_mbclen —, mblen —, _mblen_l —](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)   
 [mbstowcs —, _mbstowcs_l —](../../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)   
 [mbtowc —, _mbtowc_l —](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
 [wctomb —, _wctomb_l —](../../c-runtime-library/reference/wctomb-wctomb-l.md)   
 [Procedura WideCharToMultiByte](http://msdn.microsoft.com/library/windows/desktop/dd374130)