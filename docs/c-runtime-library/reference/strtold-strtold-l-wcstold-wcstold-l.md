---
title: strtold, _strtold_l, wcstold, _wcstold_l
ms.date: 4/2/2020
api_name:
- wcstold
- strtold
- _strtold_l
- _wcstold_l
- _o__strtold_l
- _o__wcstold_l
- _o_strtold
- _o_wcstold
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
- _tcstold_l
- _wcstold_l
- _tcstold
- strtold
- _strtold_l
- wcstold
ms.assetid: 928c0c9a-bc49-445b-8822-100eb5954115
ms.openlocfilehash: 9acc98296651f549ceffb1e1deab350a71747ea5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365364"
---
# <a name="strtold-_strtold_l-wcstold-_wcstold_l"></a>strtold, _strtold_l, wcstold, _wcstold_l

Konwertuje ciągi na długą wartość zmiennoprzecinkową o podwójnej precyzji.

## <a name="syntax"></a>Składnia

```C
long double strtold(
   const char *strSource,
   char **endptr
);
long double _strtold_l(
   const char *strSource,
   char **endptr,
   _locale_t locale
);
long double wcstold(
   const wchar_t *strSource,
   wchar_t **endptr
);
long double wcstold_l(
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

**strtold** zwraca wartość liczby zmiennoprzecinkowej jako **długie** **podwójne**, z wyjątkiem sytuacji, gdy reprezentacja spowodowałaby przepełnienie — w takim przypadku funkcja zwraca **+/- HUGE_VALL**. Znak **HUGE_VALL** odpowiada znak wartości, która nie może być reprezentowana. **strtold** zwraca wartość 0, jeśli nie można wykonać konwersji lub nastąpi niedopełnienie.

**wcstold** zwraca wartości analogicznie do **strtold**. Dla obu funkcji **errno** jest ustawiona na **ERANGE,** jeśli występuje przepełnienie lub niedopełnienie i wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w [weryfikacji parametrów](../../c-runtime-library/parameter-validation.md).

Aby uzyskać więcej informacji na temat kodów zwrotnych, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Każda funkcja konwertuje ciąg wejściowy *strSource* na **długi** **podwójny**. Funkcja **strtold** zatrzymuje odczytywanie *strSource* ciągu przy pierwszym znaku nie można rozpoznać jako część liczby. Może to być kończący się znak null. Szerokoznakowa wersja **strtold** jest **wcstold**; jego *argument strSource* jest ciągiem znaków o szerokim charakterze. W przeciwnym razie te funkcje zachowują się identycznie.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstold**|**strtold**|**strtold**|**wcstold**|
|**_tcstold_l**|**_strtold_l**|**_strtold_l**|**_wcstold_l**|

Ustawienie kategorii **LC_NUMERIC** bieżących ustawień regionalnych określa rozpoznawanie znaku radix w *strSource*. Aby uzyskać więcej informacji, zobacz [setlocale, _wsetlocale](setlocale-wsetlocale.md). Funkcje bez sufiksu **_l** używają bieżących ustawień regionalnych; **_strtold_l** i **_wcstold_l** są identyczne **z _strtold** i **_wcstold** z tą różnicą, że zamiast tego używają ustawień regionalnych, które są przekazywane. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

Jeśli *endptr* nie jest **null**, wskaźnik do znaku, który zatrzymał skanowanie jest przechowywany w miejscu, które jest wskazywane przez *endptr*. Jeśli nie można przeprowadzić konwersji (nie znaleziono prawidłowych cyfr lub określono nieprawidłową bazę), wartość *strSource* jest przechowywana w lokalizacji wskazanej przez *endptr*.

**strtold** oczekuje *strSource* wskazać ciąg następującej postaci:

[*odstępy*] [*znak*] [*cyfry*] [. *cyfry*] [ {**d** &#124; **D** &#124; **e** &#124; **E**}[*znak*]*cyfry*] ]

*Odstępy* mogą składać się ze znaków spacji i tabulacji, które są ignorowane; *znak* jest albo**+** plus (**-**) lub minus ( ); i *cyfry* są jedną lub więcej cyfr dziesiętnych. Jeśli przed znakiem radix nie pojawią się żadne cyfry, po znaku radix musi pojawić się co najmniej jedna cyfra. Po cyfrach dziesiętnych może następować wykładnik, który składa się z litery wprowadzającej (**d**, **D**, **e**lub **E**) i opcjonalnie podpisanej liczby całkowitej. Jeśli nie pojawi się ani część wykładnicza, ani znak radix, przyjmuje się, że znak radix podąża za ostatnią cyfrą w ciągu. Pierwszy znak, który nie pasuje do tego formularza, zatrzymuje skanowanie.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_strtold_l** **_strtold_l**|\<>|
|**wcstold**, **_wcstold_l**|\<> lub \<wchar.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_strtold.c
// Build with: cl /W4 /Tc crt_strtold.c
// This program uses strtold to convert a
// string to a long double-precision value.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char *string;
   char *stopstring;
   long double x;

   string = "3.1415926535898This stopped it";
   x = strtold(string, &stopstring);
   printf("string = %s\n", string);
   printf("   strtold = %.13Lf\n", x);
   printf("   Stopped scan at: %s\n\n", stopstring);
}
```

```Output
string = 3.1415926535898This stopped it
   strtold = 3.1415926535898
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
