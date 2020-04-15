---
title: strpbrk, wcspbrk, _mbspbrk, _mbspbrk_l
ms.date: 4/2/2020
api_name:
- _mbspbrk
- wcspbrk
- _mbspbrk_l
- strpbrk
- _o__mbspbrk
- _o__mbspbrk_l
api_location:
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _fstrpbrk
- _mbspbrk
- strpbrk
- _tcspbrk
- _ftcspbrk
- wcspbrk
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
ms.openlocfilehash: ecdf896587096f0370351aac07cbd6be57257305
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322168"
---
# <a name="strpbrk-wcspbrk-_mbspbrk-_mbspbrk_l"></a>strpbrk, wcspbrk, _mbspbrk, _mbspbrk_l

Skanuje ciągi znaków w określonych zestawach znaków.

> [!IMPORTANT]
> `_mbspbrk`i `_mbspbrk_l` nie może być używany w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobjęte w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
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

### <a name="parameters"></a>Parametry

*Str*<br/>
Ciąg zakończony zerem, przeszukiwany.

*strCharSet (Zestaw strCharset)*<br/>
Zestaw znaków zakończony z wartością null.

*Ustawień regionalnych*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do pierwszego wystąpienia dowolnego znaku z *strCharSet* w *str*lub wskaźnik NULL, jeśli dwa argumenty ciągu nie mają znaków wspólnych.

## <a name="remarks"></a>Uwagi

Funkcja `strpbrk` zwraca wskaźnik do pierwszego wystąpienia znaku w *str,* który należy do zestawu znaków w *strCharSet*. Wyszukiwanie nie obejmuje kończącego się znaku null.

`wcspbrk`i `_mbspbrk` są wersjami znaków szerokich i `strpbrk`wielobajtowych . Argumenty i zwracana `wcspbrk` wartość są ciągami znaków o szerokich znakach; są `_mbspbrk` ciągami znaków wielobajtowych.

`_mbspbrk`sprawdza jego parametry. Jeśli *str* lub *strCharSet* ma wartość NULL, wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w [zatwierdzeniu parametru.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, `_mbspbrk` zwraca wartość `errno` NULL i ustawia wartość EINVAL. `strpbrk`i `wcspbrk` nie weryfikują ich parametrów. Te trzy funkcje zachowują się identycznie inaczej.

`_mbspbrk`jest podobny `_mbscspn` do `_mbspbrk` z wyjątkiem tego, że zwraca wskaźnik, a nie wartość typu [size_t](../../c-runtime-library/standard-types.md).

W języku C te funkcje przyjmują **wskaźnik const** dla pierwszego argumentu. W języku C++ dostępne są dwa przeciążenia. Przeciążenie biorąc wskaźnik do **const** zwraca wskaźnik **const**; wersja, która ma wskaźnik do**non-const** zwraca wskaźnik do**non-const**. Makro _CRT_CONST_CORRECT_OVERLOADS jest zdefiniowany, jeśli dostępne są zarówno **wersje const,** jak i inne niż**const** tych funkcji. Jeśli wymagane jest zachowanie**non-const** dla obu przeciążeń C++, zdefiniuj symbol _CONST_RETURN.

Na wartość wyjściową ma wpływ ustawienie LC_CTYPE kategorii ustawień regionalnych; aby uzyskać więcej informacji, zobacz [setlocale](setlocale-wsetlocale.md). Wersje tych funkcji bez sufiksu **_l** używają bieżących ustawień regionalnych dla tego zachowania zależnego od ustawień regionalnych; wersja z sufiksem **_l** jest identyczna, z tą różnicą, że używa parametru ustawień regionalnych przekazanych zamiast. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|`_tcspbrk`|`strpbrk`|`_mbspbrk`|`wcspbrk`|
|**N/a**|**N/a**|`_mbspbrk_l`|**N/a**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|`strpbrk`|\<string.h>|
|`wcspbrk`|\<string.h> lub \<wchar.h>|
|`_mbspbrk`, `_mbspbrk_l`|\<mbstring.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
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

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Ustawienia regionalne](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcspn, wcscspn, _mbscspn, _mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[strchr, wcschr, _mbschr, _mbschr_l](strchr-wcschr-mbschr-mbschr-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
