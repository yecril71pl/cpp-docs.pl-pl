---
title: strpbrk, wcspbrk, _mbspbrk, _mbspbrk_l
ms.date: 11/04/2016
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
ms.openlocfilehash: 059b0659a8088783c6d169288de486b41a6e8d82
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50468968"
---
# <a name="strpbrk-wcspbrk-mbspbrk-mbspbrkl"></a>strpbrk, wcspbrk, _mbspbrk, _mbspbrk_l

Skanuje ciągi znaków w określonych zestawach znaków.

> [!IMPORTANT]
> `_mbspbrk` i `_mbspbrk_l` nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*str*<br/>
Ciąg zakończony znakiem null, przeszukane.

*strCharSet*<br/>
Zestaw znaków zakończony znakiem null.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do pierwszego wystąpienia dowolnego znaku z *strCharSet* w *str*, lub wskaźnika o wartości NULL, jeśli ciąg dwóch argumentów nie ma znaków wspólnych.

## <a name="remarks"></a>Uwagi

`strpbrk` Funkcja zwraca wskaźnik do pierwszego wystąpienia znaku w *str* należącej do zestawu znaków w *strCharSet*. Wyszukiwanie nie obejmuje kończącego znaku null.

`wcspbrk` i `_mbspbrk` są wersjami znaków dwubajtowych i znaków wielobajtowych `strpbrk`. Argumenty i wartość zwracana przez `wcspbrk` są znakami dwubajtowymi ciągów; te z `_mbspbrk` są ciągami znaków wielobajtowych.

`_mbspbrk` sprawdza poprawność parametrów. Jeśli *str* lub *strCharSet* ma wartość NULL, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, `_mbspbrk` zwraca wartość NULL i ustawia `errno` do EINVAL. `strpbrk` i `wcspbrk` nie sprawdzają poprawność swoich parametrów. Te trzy funkcje zachowują się identycznie.

`_mbspbrk` jest podobny do `_mbscspn` z tą różnicą, że `_mbspbrk` zwraca wskaźnik, a nie wartość typu [size_t](../../c-runtime-library/standard-types.md).

W języku C, te funkcje biorą **const** wskaźnik dla pierwszego argumentu. W języku C++ dostępne są dwa przeciążenia. Przeciążenie wskaźnika do **const** zwraca wskaźnik do **const**; wersja, która przyjmuje wskaźnik do non -**const** zwraca wskaźnik do non -**const** . _CRT_CONST_CORRECT_OVERLOADS — makro jest zdefiniowany, jeśli oba **const** i innych niż-**const** wersje tych funkcji są dostępne. Jeśli potrzebujesz non -**const** zachowanie dla obu przeciążeń C++, określ symbol _CONST_RETURN.

Wartość wyjściowa jest zależna od ustawienia LC_CTYPE ustawienia kategorii ustawień regionalnych; Aby uzyskać więcej informacji, zobacz [setlocale](setlocale-wsetlocale.md). Wersje tych funkcji, bez **_l** sufiks używają bieżących ustawień regionalnych dla zachowania zależnego od ustawień regionalnych; wersja, która **_l** sufiks jest identyczny, z tą różnicą, że użyto parametru ustawień regionalnych w zamian przekazanych. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|`_tcspbrk`|`strpbrk`|`_mbspbrk`|`wcspbrk`|
|**n/d**|**n/d**|`_mbspbrk_l`|**n/d**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|`strpbrk`|\<string.h>|
|`wcspbrk`|\<Włącz String.h > lub \<wchar.h >|
|`_mbspbrk`, `_mbspbrk_l`|\<mbstring.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz także

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcspn, wcscspn, _mbscspn, _mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[strchr, wcschr, _mbschr, _mbschr_l](strchr-wcschr-mbschr-mbschr-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
