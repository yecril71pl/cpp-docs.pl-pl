---
title: strtod, _strtod_l, wcstod, _wcstod_l
ms.date: 4/2/2020
api_name:
- wcstod
- _wcstod_l
- _strtod_l
- strtod
- _o__strtod_l
- _o__wcstod_l
- _o_strtod
- _o_wcstod
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
- api-ms-win-crt-convert-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tcstod
- strtod
- wcstod
- _strtod_l
- _wcstod_l
- stdlib/strtod
- corecrt_wstdlib/wcstod
- stdlib/_strtod_l
- corecrt_wstdlib/_wcstod_l
helpviewer_keywords:
- wcstod_l function
- tcstod_l function
- _tcstod_l function
- strtod function
- _wcstod_l function
- wcstod function
- strtod_l function
- tcstod function
- _tcstod function
- _strtod_l function
- string conversion, to floating point values
ms.assetid: 0444f74a-ba2a-4973-b7f0-1d77ba88c6ed
ms.openlocfilehash: a688846d5db4d508327745728f8933c91bfd54e0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337667"
---
# <a name="strtod-_strtod_l-wcstod-_wcstod_l"></a>strtod, _strtod_l, wcstod, _wcstod_l

Konwertuj ciągi na wartość podwójnej precyzji.

## <a name="syntax"></a>Składnia

```C
double strtod(
   const char *strSource,
   char **endptr
);
double _strtod_l(
   const char *strSource,
   char **endptr,
   _locale_t locale
);
double wcstod(
   const wchar_t *strSource,
   wchar_t **endptr
);
double wcstod_l(
   const wchar_t *strSource,
   wchar_t **endptr,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*strSource (źródło usług strSource)*<br/>
Ciąg zakończony wartością null do konwersji.

*endptr*<br/>
Wskaźnik do znaku, który zatrzymuje skanowanie.

*Ustawień regionalnych*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

**strtod** zwraca wartość liczby zmiennoprzecinkowej, z wyjątkiem sytuacji, gdy reprezentacja spowodowałaby przepełnienie, w którym to przypadku funkcja zwraca +/-**HUGE_VAL**. Znak **HUGE_VAL** odpowiada znak wartości, która nie może być reprezentowana. **strtod** zwraca wartość 0, jeśli nie można wykonać konwersji lub nastąpi niedopełnienie.

**wcstod** zwraca wartości analogicznie do **strtod**. Dla obu funkcji **errno** jest ustawiona na **ERANGE,** jeśli występuje przepełnienie lub niedopełnienie i wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w [weryfikacji parametrów](../../c-runtime-library/parameter-validation.md). Zobacz [_doserrno, errno, _sys_errlist i _sys_nerr,](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) aby uzyskać więcej informacji na temat tego i innych kodów zwrotnych.

## <a name="remarks"></a>Uwagi

Każda funkcja konwertuje ciąg wejściowy *strSource* na **podwójny**. Funkcja **strtod** konwertuje *strSource* na wartość podwójnej precyzji. **strtod** zatrzymuje odczytywanie *strSource* ciąg przy pierwszym znaku nie może rozpoznać jako część liczby. Może to być kończący się znak null. **wcstod** jest szerokoznakową wersją **strtod;** jego *argument strSource* jest ciągiem znaków o szerokim charakterze. Te funkcje zachowują się identycznie w przeciwnym razie.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstod**|**strtod**|**strtod**|**wcstod**|
|**_tcstod_l**|**_strtod_l**|**_strtod_l**|**_wcstod_l**|

Ustawienie kategorii **LC_NUMERIC** bieżących ustawień regionalnych określa rozpoznawanie znaku punktu radix w *strSource*. Aby uzyskać więcej informacji, zobacz [setlocale](setlocale-wsetlocale.md). Funkcje bez sufiksu **_l** używają bieżących ustawień regionalnych; **_strtod_l** jest identyczna **z _strtod_l** z tą różnicą, że zamiast tego używają ustawień *regionalnych* przekazanych. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

Jeśli *endptr* nie ma **wartości NULL,** wskaźnik do znaku, który zatrzymał skanowanie jest przechowywany w miejscu wskazanym przez *endptr*. Jeśli nie można przeprowadzić konwersji (nie znaleziono prawidłowych cyfr lub określono nieprawidłową bazę), wartość *strSource* jest przechowywana w lokalizacji wskazanej przez *endptr*.

**strtod** oczekuje *strSource* wskazać ciąg jednego z następujących form:

[*odstępy*] [*znak*] {*cyfry* [*cyfry radix* *digits*] &#124; *cyfry* *radix* } [{**e** &#124; **E**} [*sign*] *cyfry*] [*whitespace*] [*znak*] {**0x** &#124; **0X**} {*hexdigits* [*radix* *hexdigits*] &#124; *radix* *hexdigits*} [{**p** &#124; **P**} [*sign*] *hexdigits*] [*whitespace*] [*sign*] {**INF** &#124; **INFINITY**} [*whitespace*] [*sign*] **NAN** [*sequence*]

Opcjonalne *początkowe odstępy* mogą składać się ze znaków spacji i tabulacji, które są ignorowane; *znak* jest plus (+) lub minus (-); *cyfry* są jedną lub kilkoma cyframi dziesiętnymi; *sześciokątne* są jedną lub więcej cyfr szesnastkowych; *radix* jest znakiem punktu radix, kropką (.) w domyślnych ustawieniach regionalnych "C" lub wartością właściwą dla ustawień regionalnych, jeśli bieżące ustawienia regionalne są różne lub gdy określono *ustawienia regionalne;* *sekwencja* jest sekwencją znaków alfanumeryczne lub podkreślenia. Zarówno w postaci dziesiętnej, jak i szesnastowej, jeśli przed znakiem punktu radix nie są wyświetlane żadne cyfry, po znaku punktu radix musi pojawić się co najmniej jedna cyfra. W postaci dziesiętnej po cyfrach dziesiętnych może następować wykładnik, który składa się z litery wprowadzającej **(e** lub **E)** i opcjonalnie podpisanej liczby całkowitej. W postaci szesnastowej cyfry szesnastkowe mogą być następowane wykładnikiem, który składa się z litery wprowadzającej (**p** lub **P**) i opcjonalnie podpisanej szesnastowej liczby całkowitej reprezentującej wykładnik jako potęgę 2. W obu formach, jeśli nie pojawi się ani część wykładnicza, ani znak punktu radix, przyjmuje się, że znak punktu radix podąża za ostatnią cyfrą w ciągu. Przypadek jest ignorowany zarówno w formularzach **INF,** jak i **NAN.** Pierwszy znak, który nie pasuje do jednej z tych formularzy, zatrzymuje skanowanie.

Wersje UCRT tych funkcji nie obsługują konwersji liter wykładniczych w stylu Fortran **(d** lub **D).** To niestandardowe rozszerzenie było obsługiwane przez wcześniejsze wersje CRT i może być przełomową zmianą dla kodu. Wersje UCRT obsługują ciągi szesnastkowe i zaokrąglanie wartości INF i NAN, które nie były obsługiwane we wcześniejszych wersjach. Może to również spowodować zmiany w kodzie. Na przykład ciąg "0x1a" będzie interpretowany przez **strtod** jako 0.0 w poprzednich wersjach, ale jako 26.0 w wersji UCRT.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**strtod**, **_strtod_l**|C: &lt;stdlib.h> C++: &lt;cstdlib> &lt;lub stdlib.h> |
|**wcstod**, **_wcstod_l**|C: &lt; &lt;> lub wchar.h> C++: &lt;cstdlib>, &lt;stdlib.h> lub &lt;wchar.h> |

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_strtod.c
// This program uses strtod to convert a
// string to a double-precision value; strtol to
// convert a string to long integer values; and strtoul
// to convert a string to unsigned long-integer values.
//

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char   *string, *stopstring;
   double x;
   long   l;
   int    base;
   unsigned long ul;

   string = "3.1415926This stopped it";
   x = strtod( string, &stopstring );
   printf( "string = %s\n", string );
   printf("   strtod = %f\n", x );
   printf("   Stopped scan at: %s\n\n", stopstring );

   string = "-10110134932This stopped it";
   l = strtol( string, &stopstring, 10 );
   printf( "string = %s\n", string );
   printf("   strtol = %ld\n", l );
   printf("   Stopped scan at: %s\n\n", stopstring );

   string = "10110134932";
   printf( "string = %s\n", string );

   // Convert string using base 2, 4, and 8:
   for( base = 2; base <= 8; base *= 2 )
   {
      // Convert the string:
      ul = strtoul( string, &stopstring, base );
      printf( "   strtol = %ld (base %d)\n", ul, base );
      printf( "   Stopped scan at: %s\n", stopstring );
   }
}
```

```Output
string = 3.1415926This stopped it
   strtod = 3.141593
   Stopped scan at: This stopped it

string = -10110134932This stopped it
   strtol = -2147483648
   Stopped scan at: This stopped it

string = 10110134932
   strtol = 45 (base 2)
   Stopped scan at: 34932
   strtol = 4423 (base 4)
   Stopped scan at: 4932
   strtol = 2134108 (base 8)
   Stopped scan at: 932
```

## <a name="see-also"></a>Zobacz też

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Obsługa zmiennoprzecinkowej](../../c-runtime-library/floating-point-support.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[Ustawienia regionalne](../../c-runtime-library/locale.md)<br/>
[Ciąg do funkcji wartości liczbowej](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtol, wcstol, _strtol_l, _wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[localeconv](localeconv.md)<br/>
[_create_locale, _wcreate_locale](create-locale-wcreate-locale.md)<br/>
[_free_locale](free-locale.md)<br/>
