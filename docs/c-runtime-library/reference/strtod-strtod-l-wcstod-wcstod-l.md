---
title: strtod, _strtod_l, wcstod, _wcstod_l
description: Dokumentacja interfejsu API dla strtod, _strtod_l, wcstod i _wcstod_l; które konwertuje ciągi na wartość o podwójnej precyzji.
ms.date: 08/27/2020
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 5a791b5d0be218a49be28930c191de3eb4acf4be
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91505540"
---
# <a name="strtod-_strtod_l-wcstod-_wcstod_l"></a>strtod, _strtod_l, wcstod, _wcstod_l

Konwertuje ciągi na wartość o podwójnej precyzji.

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

*strSource*<br/>
Ciąg zakończony znakiem null do przekonwertowania.

*endptr*<br/>
Wskaźnik do znaku, który powoduje zatrzymanie skanowania.

*locale*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

**strtod** zwraca wartość liczby zmiennoprzecinkowej, z wyjątkiem sytuacji, gdy reprezentacja spowodowałoby przepełnienie, w takim przypadku funkcja zwraca wartość +/-**HUGE_VAL**. Znak **HUGE_VAL** jest zgodny ze znakiem wartości, która nie może być reprezentowana. **strtod** zwraca `0` , jeśli konwersja nie może być wykonana lub występuje niedopełnienie.

**wcstod** zwraca wartości analogicznie do **strtod**:

- Dla obu funkcji **errno** jest ustawiony na **ERANGE** , jeśli występuje przepełnienie lub nadmiar.
- Jeśli istnieją nieprawidłowe parametry, **errno** jest ustawiona na **EINVAL** i zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md).

Aby uzyskać więcej informacji na temat tego i innych kodów powrotnych, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Każda funkcja konwertuje ciąg wejściowy *strSource* na **`double`** . Funkcja **strtod** konwertuje *strSource* na wartość o podwójnej precyzji. **strtod** przestaje odczytywania ciągu *strSource* przy pierwszym znaku, którego nie można rozpoznać jako części liczby. Ten znak może być końcowym znakiem null. **wcstod** to dwubajtowa wersja **strtod**; jego argument *strSource* jest ciągiem znaków dwubajtowych. Funkcje te zachowują się identycznie w inny sposób.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _MBCS _UNICODE &|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstod**|**strtod**|**strtod**|**wcstod**|
|**_tcstod_l**|**_strtod_l**|**_strtod_l**|**_wcstod_l**|

Ustawienie kategorii **LC_NUMERIC** bieżących ustawień regionalnych określa rozpoznawanie znaku punktu podstawy w *strSource*. Aby uzyskać więcej informacji, zobacz [setlocale](setlocale-wsetlocale.md). Funkcje bez sufiksu **_l** używają bieżących ustawień regionalnych; **_strtod_l** jest taka sama jak **_strtod** , z wyjątkiem tego, że poprzednie używa przekazaną w zamian *ustawień regionalnych* . Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

Jeśli *endptr* nie ma **wartości null**, wskaźnik do znaku, który zatrzymał skanowanie jest przechowywany w lokalizacji wskazywanej przez *endptr*. Jeśli konwersja nie może być wykonywana (nie znaleziono prawidłowych cyfr lub określono nieprawidłową podstawę), wartość *strSource* jest przechowywana w lokalizacji wskazywanej przez *endptr*.

**strtod** oczekuje, że *strSource* , aby wskazywały ciąg jednej z następujących form:

[*odstęp*] [*Sign*] {*cyfry* [*radix* *cyfry*podstawy] &#124; *podstawy* *cyfr*} [{**e** &#124; **e**} [*Sign*] *cyfry*] [*odstępy*] [*Sign*] {*sequence***0x** &#124; **0x**} {*hexdigits* [*podstawy* *hexdigits*] &#124; *podstawy* *hexdigits*} [{**p** &#124; **p**} [*Sign*] *cyfry*] [*odstęp**] [**Sign* **] {** **inf** &#124; **nieskończoność***whitespace*

Opcjonalne *odstępy* wiodące mogą zawierać spacje i znaki tabulacji, które są ignorowane. \
*znak* jest znakiem plus (+) lub minus (-). \
*cyfry* są co najmniej jedną cyfrą dziesiętną. \
*hexdigits* to jedna lub więcej cyfr szesnastkowych. \
*podstawy* jest znakiem punktu podstawy, kropką (.) w domyślnych ustawieniach regionalnych "C" lub wartość specyficzną dla ustawień regionalnych, jeśli bieżące ustawienia regionalne są różne lub jeśli określono *Ustawienia regionalne* . \
 *Sekwencja* jest sekwencją znaków alfanumerycznych lub podkreślenia.

W formularzach liczb dziesiętnych i szesnastkowych, jeśli żadne cyfry nie pojawiają się przed znakiem punktu podstawy, co najmniej jeden musi występować po znaku podstawy.

W postaci dziesiętnej cyfry dziesiętne mogą następować według wykładnika, która składa się z litery wprowadzającej (**e** lub **e**) i opcjonalnie podpisanej liczby całkowitej.

W postaci szesnastkowej cyfry szesnastkowe mogą następować przy użyciu wykładnika, która składa się z litery wprowadzającej (**p** lub **p**) i opcjonalnie podpisanej dziesiętnej liczby całkowitej, która reprezentuje wykładnik jako potęgę 2.

W obu formularzach, jeśli nie ma części wykładnika lub podstawy znaku, przyjmuje się, że znak punktu podstawy jest zgodny z ostatnią cyfrą w ciągu.

Wielkość liter jest ignorowana w formularzach **inf** i **NaN** . Pierwszy znak, który nie pasuje do jednego z tych formularzy, uniemożliwia skanowanie.

Wersje UCRT tych funkcji nie obsługują konwersji liter wykładnika Pascal (**d** lub **d**). To niestandardowe rozszerzenie było obsługiwane przez wcześniejsze wersje CRT i może być istotną zmianą dla kodu. Wersje UCRT obsługują ciągi szesnastkowe i dwukierunkowe wartości plików INF i NAN, które nie były obsługiwane we wcześniejszych wersjach. Może to również spowodować istotne zmiany w kodzie. Na przykład ciąg "0x1A" byłby interpretowany przez **strtod** jako 0,0 w poprzednich wersjach, ale jako 26,0 w wersji UCRT.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**strtod**, **_strtod_l**|C: &lt; STDLIB. h> C++: &lt; cstdlib> lub &lt; stdlib. h> |
|**wcstod**, **_wcstod_l**|C: &lt; STDLIB. h> lub &lt; WCHAR. h> C++: &lt; cstdlib>, &lt; STDLIB. h> lub &lt; WCHAR. h> |

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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
[Obsługa zmiennoprzecinkowa](../../c-runtime-library/floating-point-support.md)<br/>
[Interpretacja sekwencji znaków wielobajtowych](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[Ustawienie](../../c-runtime-library/locale.md)<br/>
[Funkcje ciągu do wartości numerycznych](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtol, wcstol, _strtol_l, _wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[localeconv](localeconv.md)<br/>
[_create_locale, _wcreate_locale](create-locale-wcreate-locale.md)<br/>
[_free_locale](free-locale.md)<br/>
