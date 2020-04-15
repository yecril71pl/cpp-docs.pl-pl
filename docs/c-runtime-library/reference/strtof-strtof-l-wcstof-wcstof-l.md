---
title: strtof, _strtof_l, wcstof, _wcstof_l
ms.date: 4/2/2020
api_name:
- _strtof_l
- wcstof
- strtof
- _wcstof_l
- _o__strtof_l
- _o__wcstof_l
- _o_strtof
- _o_wcstof
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
- _tcstof
- _tcstof_l
- stdlib/strtof
- strtof
- stdlib/_strtof_l
- _strtof_l
- corecrt_wstdlib/wcstof
- wcstof
- corecrt_wstdlib/_wcstof_l
- _wcstof_l
helpviewer_keywords:
- _strtof_l function
- _tcstof function
- _wcstof_l function
- wcstof function
- _tcstof_l function
- strtof function
ms.assetid: 52221b46-876d-4fcc-afb1-97512c17a43b
ms.openlocfilehash: f61aa0edeadd74a254f906dd745e18b059da7f24
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365147"
---
# <a name="strtof-_strtof_l-wcstof-_wcstof_l"></a>strtof, _strtof_l, wcstof, _wcstof_l

Konwertuje ciągi na wartość zmiennoprzecinkową o pojedynczej precyzji.

## <a name="syntax"></a>Składnia

```C
float strtof(
   const char *strSource,
   char **endptr
);
float _strtof_l(
   const char *strSource,
   char **endptr,
   _locale_t locale
);
float wcstof(
   const wchar_t *strSource,
   wchar_t **endptr
);
float wcstof_l(
   const wchar_t *strSource,
   wchar_t **endptr,
   _locale_t locale
);
```

## <a name="parameters"></a>Parametry

*strSource (źródło usług strSource)*<br/>
Ciąg zakończony wartością null do konwersji.

*endptr*<br/>
Wskaźnik do znaku, który zatrzymuje skanowanie.

*Ustawień regionalnych*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

**strtof** zwraca wartość liczby zmiennoprzecinkowej, z wyjątkiem sytuacji, gdy reprezentacja spowodowałaby przepełnienie, w którym to przypadku funkcja zwraca +/-**HUGE_VALF**. Znak **HUGE_VALF** odpowiada znak wartości, która nie może być reprezentowana. **strtof** zwraca wartość 0, jeśli nie można wykonać konwersji lub nastąpi niedopełnienie.

**wcstof** zwraca wartości analogicznie do **strtof**. Dla obu funkcji **errno** jest ustawiona na **ERANGE,** jeśli występuje przepełnienie lub niedopełnienie i wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w [weryfikacji parametrów](../../c-runtime-library/parameter-validation.md).

Aby uzyskać więcej informacji na temat kodów zwrotnych, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Każda funkcja konwertuje ciąg wejściowy *strSource* na **float**. Funkcja **strtof** konwertuje *strSource* na wartość pojedynczej precyzji. **strtof** zatrzymuje odczytywanie *strSource* ciąg przy pierwszym znaku nie może rozpoznać jako część liczby. Może to być kończący się znak null. **wcstof** jest szerokoznakową wersją **strtof;** jego *argument strSource* jest ciągiem znaków o szerokim charakterze. W przeciwnym razie te funkcje zachowują się identycznie.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstof**|**strtof**|**strtof**|**wcstof**|
|**_tcstof_l**|**_strtof_l**|**_strtof_l**|**_wcstof_l**|

Ustawienie kategorii **LC_NUMERIC** bieżących ustawień regionalnych określa rozpoznawanie znaku radix w *strSource*; aby uzyskać więcej informacji, zobacz [setlocale, _wsetlocale](setlocale-wsetlocale.md). Funkcje, które nie mają sufiksu **_l,** używają bieżących ustawień regionalnych; te, które mają sufiks są identyczne, z tą różnicą, że używają ustawień regionalnych, które są przekazywane zamiast. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

Jeśli *endptr* nie jest **null**, wskaźnik do znaku, który zatrzymał skanowanie jest przechowywany w miejscu, które jest wskazywane przez *endptr*. Jeśli nie można przeprowadzić konwersji (nie znaleziono prawidłowych cyfr lub określono nieprawidłową bazę), wartość *strSource* jest przechowywana w lokalizacji wskazanej przez *endptr*.

**strtof** oczekuje *strSource* wskazać ciąg następującej postaci:

[*odstępy*] [*znak*] [*cyfry*] [__.__ *cyfry*] [{**e** &#124; **E**} [*znak*] *cyfry*]

*Odstępy* mogą składać się ze znaków spacji i tabulacji, które są ignorowane; *znak* jest albo**+** plus (**-**) lub minus ( ); i *cyfry* są jedną lub więcej cyfr dziesiętnych. Jeśli przed znakiem radix nie pojawią się żadne cyfry, po znaku radix musi pojawić się co najmniej jedna cyfra. Po cyfrach dziesiętnych może następować wykładnik, który składa się z litery wprowadzającej **(e** lub **E)** i opcjonalnie podpisanej liczby całkowitej. Jeśli nie pojawi się ani część wykładnicza, ani znak radix, przyjmuje się, że znak radix podąża za ostatnią cyfrą w ciągu. Pierwszy znak, który nie pasuje do tego formularza, zatrzymuje skanowanie.

Wersje UCRT tych funkcji nie obsługują konwersji liter wykładniczych w stylu Fortran **(d** lub **D).** To niestandardowe rozszerzenie było obsługiwane przez wcześniejsze wersje CRT i może być przełomową zmianą dla kodu.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**strtof**, **_strtof_l**|C: \<stdlib.h> C++: &lt;cstdlib> \<lub stdlib.h>|
|**wcstof**, **_wcstof_l**|C: \< \<> lub wchar.h> C++: &lt;cstdlib>, \<stdlib.h> lub \<wchar.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_strtof.c
// This program uses strtof to convert a
// string to a single-precision value.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char *string;
   char *stopstring;
   float x;

   string = "3.14159This stopped it";
   x = strtof(string, &stopstring);
   printf("string = %s\n", string);
   printf("   strtof = %f\n", x);
   printf("   Stopped scan at: %s\n\n", stopstring);
}
```

```Output
string = 3.14159This stopped it
   strtof = 3.141590
   Stopped scan at: This stopped it
```

## <a name="see-also"></a>Zobacz też

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Obsługa zmiennoprzecinkowej](../../c-runtime-library/floating-point-support.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[Ustawienia regionalne](../../c-runtime-library/locale.md)<br/>
[Ciąg do funkcji wartości liczbowej](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtol, wcstol, _strtol_l, _wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[localeconv](localeconv.md)<br/>
[_create_locale, _wcreate_locale](create-locale-wcreate-locale.md)<br/>
[_free_locale](free-locale.md)<br/>
