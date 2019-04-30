---
title: strtod, _strtod_l, wcstod, _wcstod_l
ms.date: 10/20/2017
apiname:
- wcstod
- _wcstod_l
- _strtod_l
- strtod
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
ms.openlocfilehash: c8c2b3b491e2e7265829fa88580529dc757ace8c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62376474"
---
# <a name="strtod-strtodl-wcstod-wcstodl"></a>strtod, _strtod_l, wcstod, _wcstod_l

Konwertowanie ciągów na wartości podwójnej precyzji.

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
Ciąg zakończony wartością null do konwersji.

*endptr*<br/>
Wskaźnik znaku zatrzymującego skanowanie.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

**strtod** zwraca wartość zmiennoprzecinkową, z wyjątkiem sytuacji, gdy ta reprezentacja spowodowałoby przepełnienie, w których przypadku funkcja zwraca wartość +/-**HUGE_VAL**. Znak **HUGE_VAL** odpowiada znakowi wartości, który nie może być reprezentowana. **strtod** zwraca wartość 0, jeśli nie można wykonać konwersji lub występuje niedopełnienie.

**wcstod —** zwraca wartości analogicznie do **strtod**. Dla obu funkcji **errno** ustawiono **ERANGE** Jeśli występuje przepełnienie lub niedopełnienie i wywołany nieprawidłowy parametr uchwytu, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Aby uzyskać więcej informacji na ten temat i inne kody powrotne.

## <a name="remarks"></a>Uwagi

Każda funkcja konwertuje ciąg wejściowy *strSource* do **double**. **Strtod** funkcji konwertuje *strSource* wartość podwójnej precyzji. **strtod** przestaje odczytywać ciąg *strSource* przy pierwszym znaku, nie może rozpoznać jako elementu liczby. Może to być kończący znak null. **wcstod —** to wersja znaku dwubajtowego **strtod**; jej *strSource* argumentu jest ciągiem znaku dwubajtowego. Funkcje te zachowują się identycznie.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstod —**|**strtod**|**strtod**|**wcstod**|
|**_tcstod_l**|**_strtod_l**|**_strtod_l**|**_wcstod_l**|

**LC_NUMERIC** ustawienie kategorii bieżących ustawień regionalnych określa rozpoznawanie znaku podstawy w parametrze punktu *strSource*. Aby uzyskać więcej informacji, zobacz [setlocale](setlocale-wsetlocale.md). Funkcje bez **_l** sufiksa używa bieżących ustawień regionalnych; **_strtod_l —** jest taka sama jak **_strtod_l —** z tą różnicą, że używają one *ustawień regionalnych* przekazanych w zamian. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

Jeśli *endptr* nie **NULL**, wskaźnik znaku, który zatrzymał skanowanie jest przechowywany w lokalizacji wskazywanej przez *endptr*. Jeśli konwersja nie może być wykonywana (nie znaleziono żadnych prawidłowych cyfr lub określono nieprawidłową podstawę), wartość *strSource* jest przechowywany w lokalizacji wskazywanej przez *endptr*.

**strtod** oczekuje *strSource* do wskaże ciąg z jednej z następujących form:

[*odstępu*] [*logowania*] {*cyfr* [*podstawy* *cyfr*] &#124;  *podstawy* *cyfr*} [{**e** &#124; **E**} [*logowania*] *cyfr*] [*odstępu*] [*logowania*] {**0 x** &#124; **0 X**} {*cyfry_szesnastkowe* [ *podstawy* *cyfry_szesnastkowe*] &#124; *podstawy* *cyfry_szesnastkowe*} [{**p** &#124; **P**} [*logowania*] *cyfry_szesnastkowe*] [*odstępu*] [*logowania*] { **INF** &#124; **NIESKOŃCZONOŚCI**} [*odstępu*] [*logowania*]  **NAN** [*sekwencji*]

Opcjonalne wiodących *odstępu* może składać się ze znaków spacji lub tabulatora, które są ignorowane. *logowania* jest plus (+) lub minus (-); *cyfr* są co najmniej jedna cyfra dziesiętna; *cyfry_szesnastkowe* są co najmniej jedna cyfra szesnastkowa; *podstawy* to podstawy punkt znak kropki (.) w domyślnych ustawień regionalnych "C", lub wartość specyficzne dla ustawień regionalnych, jeśli różni się bieżących ustawień regionalnych, lub gdy *ustawień regionalnych* jest określona; *sekwencji* jest sekwencją alfanumerycznych lub znaki podkreślenia. W formularzach zarówno dziesiętną, a szesnastkową liczb Jeśli żadna cyfra pojawia się przed znakiem podstawy punktu, co najmniej jeden musi występować po znaku podstawy w punkcie. W formie dziesiętnej cyfr dziesiętnych może następować wykładnik, który składa się z litery wprowadzającej (**e** lub **E**) i opcjonalnie podpisanej liczby całkowitej. W postaci szesnastkowej cyfr szesnastkowych może następować wykładnik, który składa się z litery wprowadzającej (**p** lub **P**) i opcjonalnie Szesnastkowa liczba całkowita ze znakiem reprezentuje wykładnik jako potęgą liczby 2. W dowolnej postaci wykładnik ani znak podstawy punkt nie jest wyświetlana, znak podstawy punkt jest traktowana jako ostatniej cyfrze w ciągu. Wielkość liter jest ignorowana w obu **INF** i **NAN** formularzy. Pierwszy znak, który nie pasuje do jednej z poniższych metod zatrzymuje skanowanie.

UCRT wersje tych funkcji nie obsługują konwersję Fortran stylu (**d** lub **D**) litery wykładnika. To rozszerzenie niestandardowe była obsługiwana przez wcześniejsze wersje CRT i może być istotnej zmiany w kodzie. Wersji 140_xp Biblioteka UCRT obsługują ciągów szesnastkowych i Pełna zgodnooć wersji INF i NAN wartości, które nie są obsługiwane we wcześniejszych wersjach. Ponadto może to spowodować przełomowe zmiany w kodzie. Na przykład ciąg "0x1a" może być interpretowany przez **strtod** jako 0.0 w poprzednich wersjach, ale jako 26.0 w wersji 140_xp Biblioteka UCRT.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**strtod**, **_strtod_l —**|C: &lt;stdlib.h > C++: &lt;cstdlib — > lub &lt;stdlib.h > |
|**wcstod —**, **_wcstod_l —**|C: &lt;stdlib.h> or &lt;wchar.h> C++: &lt;cstdlib>, &lt;stdlib.h> or &lt;wchar.h> |

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz także

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[Konwertowanie ciągów na wartości](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtol, wcstol, _strtol_l, _wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[localeconv](localeconv.md)<br/>
[_create_locale, _wcreate_locale](create-locale-wcreate-locale.md)<br/>
[_free_locale](free-locale.md)<br/>
