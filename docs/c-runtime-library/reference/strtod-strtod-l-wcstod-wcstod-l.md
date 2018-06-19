---
title: strtod —, _strtod_l —, wcstod —, _wcstod_l — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/20/2017
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9abf6ea87681470f4e1d290a9a0059efb41de499
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32417494"
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
Zerem ciąg do konwersji.

*endptr*<br/>
Wskaźnik do znaku, który zatrzymuje skanowania.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

**strtod —** zwraca wartość liczby zmiennoprzecinkowej, z wyjątkiem przypadków, gdy reprezentacja mogłoby spowodować przepełnienie, w którego przypadku funkcja zwraca +/-**huge_val —**. Znak **huge_val —** znak wartość, która nie może być przedstawiony jest zgodna. **strtod —** zwraca wartość 0, jeśli konwersja nie można wykonać lub niedopełnienie występuje.

**wcstod —** zwraca wartości analogously do **strtod —**. Dla obu tych funkcji **errno** ustawiono **erange —** Jeśli występuje przepełnienie lub niedomiar i program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Aby uzyskać więcej informacji na ten temat oraz inne kody powrotu.

## <a name="remarks"></a>Uwagi

Funkcja każdego konwertuje ciąg wejściowy *strSource* do **podwójne**. **Strtod —** funkcji konwertuje *strSource* wartość podwójnej precyzji. **strtod —** przestaje czytać ciąg *strSource* pierwszego znaku nie jest rozpoznawana jako część liczby. Może to być znak końcowy null. **wcstod —** jest wersja znaków dwubajtowych **strtod —**; *strSource* argument jest ciąg znaków dwubajtowych. Funkcje te działają tak samo w przeciwnym razie wartość.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstod —**|**strtod**|**strtod**|**wcstod**|
|**_tcstod_l —**|**_strtod_l**|**_strtod_l**|**_wcstod_l**|

**Lc_numeric —** ustawienie kategorii bieżące ustawienia regionalne określa rozpoznawania podstawa punkt znak w *strSource*. Aby uzyskać więcej informacji, zobacz [setlocale](setlocale-wsetlocale.md). Funkcje bez **_l** sufiks Użyj bieżących ustawień regionalnych; **_strtod_l —** jest taka sama jak **_strtod_l —** z tą różnicą, że używają one *ustawień regionalnych* przekazany w zamian. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

Jeśli *endptr* nie jest **NULL**, wskaźnik do znaku zatrzymania skanowania są przechowywane w lokalizacji wskazywanej przez *endptr*. Jeśli konwersja nie można wykonać (nie znaleziono żadnych prawidłowych cyfr lub określono nieprawidłowy atrybut podstawowy), wartość *strSource* są przechowywane w lokalizacji wskazywanej przez *endptr*.

**strtod —** oczekuje *strSource* wskaż ciąg jednego z następujących formatów:

[*odstępem*] [*znak*] {*cyfr* [*radix* *cyfr*] &#124;  *Podstawa* *cyfr*} [{**e** &#124; **E**} [*znak*] *cyfr*] [*odstępem*] [*znak*] {**0 x** &#124; **0 X**} {*hexdigits* [ *radix* *hexdigits*] &#124; *radix* *hexdigits*} [{**p** &#124; **P**} [*znak*] *hexdigits*] [*odstępem*] [*znak*] { **INF** &#124; **NIESKOŃCZONOŚCI**} [*odstępem*] [*znak*]  **NAN** [*sekwencji*]

Opcjonalne wiodące *odstępem* może zawierać znaków miejsca i karty, które są ignorowane. *znak* jest plus (+) lub minus (-); *cyfr* są co najmniej jeden cyfr dziesiętnych; *hexdigits* są co najmniej jedną cyfrę szesnastkową; *radix* jest podstawa punkt znak kropki (.) w domyślnych ustawień regionalnych "C", lub wartości ustawień regionalnych, gdy bieżące ustawienia regionalne jest inny, lub gdy *ustawień regionalnych* jest określona; *sekwencji* jest sekwencją alfanumeryczne lub znaki podkreślenia. W zarówno dziesiętnej i szesnastkowej formy liczb Jeśli cyfr nie pojawiają się przed znakiem punktu podstawa, co najmniej jeden musi występować po znaku podstawa punktu. W formularzu dziesiętną cyfr dziesiętnych może nastąpić wykładnik, obejmującego wprowadzające litery (**e** lub **E**) i opcjonalnie całkowita. W formacie szesnastkowym cyfr szesnastkowych może następować wykładnik, obejmującego wprowadzające litery (**p** lub **P**) i opcjonalnie szesnastkową liczby całkowite ze znakiem reprezentuje wykładnik jako potęgą liczby 2. W obu formularzy wykładnika części ani znaków punktu podstawa zostanie wyświetlone, znak punktu podstawa jest traktowana jako wykonaj ostatnich cyfr w ciągu. Wielkość liter jest ignorowana w obu **INF** i **NAN** formularzy. Pierwszy znak, który nie pasuje do jednej z tych form zatrzymuje skanowania.

Biblioteka UCRT wersje tych funkcji nie obsługują konwersji Fortran stylu (**d** lub **D**) wykładnika litery. To rozszerzenie niestandardowe była obsługiwana przez wcześniejsze wersje CRT i może być istotne zmiany kodu. Wersje Biblioteka UCRT obsługują ciągów szesnastkowych i dwustronną komunikację INF i NAN wartości, które nie są obsługiwane we wcześniejszych wersjach. To może powodować również istotne zmiany w kodzie. Na przykład ciąg "0x1a" może zostać zinterpretowany przez **strtod —** jako 0,0 w poprzednich wersjach, ale jako 26.0 w wersji Biblioteka UCRT.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**strtod —**, **_strtod_l —**|C: &lt;stdlib.h > C++: &lt;cstdlib — > lub &lt;stdlib.h > |
|**wcstod —**, **_wcstod_l —**|C: &lt;stdlib.h > lub &lt;wchar.h > C++: &lt;cstdlib — >, &lt;stdlib.h > lub &lt;wchar.h > |

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
