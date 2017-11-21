---
title: "strpbrk —, wcspbrk —, _mbspbrk —, _mbspbrk_l — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _mbspbrk
- wcspbrk
- _mbspbrk_l
- strpbrk
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _fstrpbrk
- _mbspbrk
- strpbrk
- _tcspbrk
- _ftcspbrk
- wcspbrk
dev_langs: C++
helpviewer_keywords:
- fstrpbrk function
- _ftcspbrk function
- _mbspbrk_l function
- strpbrk function
- _fstrpbrk function
- mbspbrk function
- characters [C++], scanning strings
- _tcspbrk function
- wcspbrk function
- ftcspbrk function
- character sets [C++], scanning strings for characters
- strings [C++], scanning
- tcspbrk function
- _mbspbrk function
- mbspbrk_l function
ms.assetid: 80b504f7-a167-4dde-97ad-4ae3000dc810
caps.latest.revision: "30"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: aef34a8cddfde1088c8535a1835b157146400faa
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="strpbrk-wcspbrk-mbspbrk-mbspbrkl"></a>strpbrk, wcspbrk, _mbspbrk, _mbspbrk_l
Skanowanie ciągów znaków w określonych zestawów znaków.  
  
> [!IMPORTANT]
>  `_mbspbrk`i `_mbspbrk_l` nie można używać w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane z parametrem /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Składnia  
  
```  
char *strpbrk(  
   const char *str,  
   const char *strCharSet   
); // C only  
char *strpbrk(  
   char *str,  
   const char *strCharSet   
); // C++ only  
const char *strpbrk(  
   const char *str,  
   const char *strCharSet   
); // C++ only  
wchar_t *wcspbrk(  
   const wchar_t *str,  
   const wchar_t *strCharSet   
); // C only  
wchar_t *wcspbrk(  
   wchar_t *str,  
   const wchar_t *strCharSet   
); // C++ only  
const wchar_t *wcspbrk(  
   const wchar_t *str,  
   const wchar_t *strCharSet   
); // C++ only  
unsigned char *_mbspbrk(  
   const unsigned char *str,  
   const unsigned char *strCharSet   
); // C only  
unsigned char *_mbspbrk(  
   unsigned char *str,  
   const unsigned char *strCharSet   
); // C++ only  
const unsigned char *_mbspbrk(  
   const unsigned char *str,  
   const unsigned char *strCharSet   
); // C++ only  
unsigned char *_mbspbrk_l(  
   const unsigned char *str,  
   const unsigned char *strCharSet,  
   _locale_t locale  
); // C only  
unsigned char *_mbspbrk_l(  
   unsigned char *str,  
   const unsigned char *strCharSet,  
   _locale_t locale  
); // C++ only  
const unsigned char *_mbspbrk_l(  
   const unsigned char *str,  
   const unsigned char* strCharSet,  
   _locale_t locale  
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 `str`  
 Ciąg zerem, przeszukiwane.  
  
 `strCharSet`  
 Zestaw znaków zakończony znakiem null.  
  
 `locale`  
 Ustawienia regionalne do użycia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wskaźnik do pierwszego wystąpienia dowolnego znaku z `strCharSet` w `str`, lub `NULL` wskaźnika, jeśli ciąg dwa argumenty mają wspólną żadne znaki.  
  
## <a name="remarks"></a>Uwagi  
 `strpbrk` Funkcja zwraca wskaźnik do pierwszego wystąpienia znaku w `str` należący do zbioru znaków `strCharSet`. Wyszukiwanie nie zawiera znak końcowy null.  
  
 `wcspbrk`i `_mbspbrk` znaków dwubajtowych i znaków wielobajtowych wersji `strpbrk`. Argumenty i zwracana wartość `wcspbrk` są znaków dwubajtowych ciągi; tych `_mbspbrk` są ciągami znaków wielobajtowych.  
  
 `_mbspbrk`sprawdza poprawność parametrów. Jeśli `str` lub `strCharSet` jest `NULL`, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, `_mbspbrk` zwraca `NULL` i ustawia `errno` do `EINVAL`. `strpbrk`i `wcspbrk` nie weryfikują ich parametrów. Te trzy funkcje działają tak samo w przeciwnym razie wartość.  
  
 `_mbspbrk`przypomina `_mbscspn` z tą różnicą, że `_mbspbrk` zwraca wskaźnik zamiast wartości typu [size_t](../../c-runtime-library/standard-types.md).  
  
 W języku C, te funkcje pobierać `const` wskaźnik dla pierwszego argumentu. W języku C++ dostępne są dwa przeciążenia. Biorąc wskaźnik do przeciążenia `const` zwraca wskaźnik do `const`; wersję, która przyjmuje wskaźnik do innego niż`const` zwraca wskaźnik do innego niż`const`. Makro `_CRT_CONST_CORRECT_OVERLOADS` jest zdefiniowana, jeśli obie `const` i nie-`const` są dostępne wersje tych funkcji. Jeśli potrzebujesz nienależących`const` zachowanie dla obu przeciążeń C++, zdefiniuj symbol `_CONST_RETURN`.  
  
 Wartość wyjściowa jest zagrożony ustawienie `LC_CTYPE` kategorii ustawienie ustawień regionalnych; Aby uzyskać więcej informacji, zobacz [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md). Wersje tych funkcji bez `_l` Użyj sufiksu bieżące ustawienia regionalne tego zachowania zależnych od ustawień regionalnych; wersja z `_l` sufiks jest identyczny z tą różnicą, że zamiast przekazany parametr ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcspbrk`|`strpbrk`|`_mbspbrk`|`wcspbrk`|  
|**n/d**|**n/d**|`_mbspbrk_l`|**n/d**|  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`strpbrk`|\<String.h >|  
|`wcspbrk`|\<String.h > lub \<wchar.h >|  
|`_mbspbrk`, `_mbspbrk_l`|\<mbstring.h >|  
  
 Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Przykład  
  
```  
// crt_strpbrk.c  
  
#include <string.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char string[100] = "The 3 men and 2 boys ate 5 pigs\n";  
   char *result = NULL;  
  
   // Return pointer to first digit in "string".  
   printf( "1: %s\n", string );  
   result = strpbrk( string, "0123456789" );  
   printf( "2: %s\n", result++ );  
   result = strpbrk( result, "0123456789" );  
   printf( "3: %s\n", result++ );  
   result = strpbrk( result, "0123456789" );  
   printf( "4: %s\n", result );  
}  
```  
  
```Output  
1: The 3 men and 2 boys ate 5 pigs  
  
2: 3 men and 2 boys ate 5 pigs  
  
3: 2 boys ate 5 pigs  
  
4: 5 pigs  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)   
 [Ustawienia regionalne](../../c-runtime-library/locale.md)   
 [Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [strcspn —, wcscspn —, _mbscspn — _mbscspn_l —](../../c-runtime-library/reference/strcspn-wcscspn-mbscspn-mbscspn-l.md)   
 [strchr —, wcschr —, _mbschr — _mbschr_l —](../../c-runtime-library/reference/strchr-wcschr-mbschr-mbschr-l.md)   
 [strrchr —, wcsrchr —, _mbsrchr — _mbsrchr_l —](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)