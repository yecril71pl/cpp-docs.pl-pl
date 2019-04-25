---
title: strtold, _strtold_l, wcstold, _wcstold_l
ms.date: 04/05/2018
apiname:
- wcstold
- strtold
- _strtold_l
- _wcstold_l
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
- _tcstold_l
- _wcstold_l
- _tcstold
- strtold
- _strtold_l
- wcstold
ms.assetid: 928c0c9a-bc49-445b-8822-100eb5954115
ms.openlocfilehash: dcf1eca5b163c8553b43d747d53537ec424a793c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62269192"
---
# <a name="strtold-strtoldl-wcstold-wcstoldl"></a>strtold, _strtold_l, wcstold, _wcstold_l

Konwertuje ciągi na wartość zmiennoprzecinkową długa podwójnej precyzji.

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

*strSource*<br/>
Ciąg zakończony wartością null do konwersji.

*endptr*<br/>
Wskaźnik znaku zatrzymującego skanowanie.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

**strtold** zwraca wartość zmiennoprzecinkową jako **długie** **double**, z wyjątkiem sytuacji, gdy ta reprezentacja spowodowałoby przepełnienie — w takim przypadku funkcja zwraca wartość +/-**HUGE_VALL**. Znak **HUGE_VALL** odpowiada znakowi wartości, który nie może być reprezentowana. **strtold** zwraca wartość 0, jeśli nie można wykonać konwersji lub występuje niedopełnienie.

**wcstold** zwraca wartości analogicznie do **strtold**. Dla obu funkcji **errno** ustawiono **ERANGE** Jeśli występuje przepełnienie lub niedopełnienie i wywołany nieprawidłowy parametr uchwytu, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md).

Aby uzyskać więcej informacji na temat kodów powrotnych, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Każda funkcja konwertuje ciąg wejściowy *strSource* do **długie** **double**. **Strtold** funkcja przestaje odczytywać ciąg *strSource* przy pierwszym znaku, nie może rozpoznać jako elementu liczby. Może to być kończący znak null. Wersja znaków dwubajtowych **strtold** jest **wcstold**; jej *strSource* argumentu jest ciągiem znaku dwubajtowego. W przeciwnym wypadku te funkcje zachowują się identycznie.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstold**|**strtold**|**strtold**|**wcstold**|
|**_tcstold_l**|**_strtold_l**|**_strtold_l**|**_wcstold_l**|

**LC_NUMERIC** ustawienie kategorii bieżących ustawień regionalnych określa rozpoznawanie znaku podstawy w parametrze *strSource*. Aby uzyskać więcej informacji, zobacz [setlocale, _wsetlocale](setlocale-wsetlocale.md). Funkcje bez **_l** sufiksa używa bieżących ustawień regionalnych; **_strtold_l** i **_wcstold_l** są takie same jak **_strtold** i **_wcstold** z tą różnicą, że używają w zamian ustawień regionalnych to przekazana. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

Jeśli *endptr* nie **NULL**, wskaźnik znaku, który zatrzymał skanowanie jest przechowywany w lokalizacji, która jest wskazywany przez *endptr*. Jeśli konwersja nie może być wykonywana (nie znaleziono żadnych prawidłowych cyfr lub określono nieprawidłową podstawę), wartość *strSource* znajduje się w lokalizacji, która jest wskazywany przez *endptr*.

**strtold** oczekuje *strSource* do wskaże ciąg o następującej postaci:

[*odstępu*] [*logowania*] [*cyfr*] [. *cyfry*] [{**d** &#124; **D** &#124; **e** &#124; **E**} [*logowania* ]*cyfr*]

A *odstępu* może składać się ze znaków spacji lub tabulatora, które są ignorowane. *logowania* jest plus (**+**) lub minus (**-**); i *cyfr* są co najmniej jedna cyfra dziesiętna. Jeśli żadna cyfra pojawia się przed znakiem podstawy, co najmniej jedna musi występować po znaku podstawy. Cyfr dziesiętnych może następować wykładnik, który składa się z litery wprowadzającej (**d**, **D**, **e**, lub **E**) i opcjonalnie liczby całkowitej ze znakiem. Jeśli wykładnik ani znak podstawy nie pojawia się, znak podstawy zakłada się, że ostatniej cyfrze w ciągu. Pierwszy znak, który nie mieści się tym formularzu zatrzymuje skanowanie.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**strtold**, **_strtold_l**|\<stdlib.h>|
|**wcstold**, **_wcstold_l**|\<stdlib.h> or \<wchar.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz także

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[Konwertowanie ciągów na wartości](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtol, wcstol, _strtol_l, _wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[localeconv](localeconv.md)<br/>
[_create_locale, _wcreate_locale](create-locale-wcreate-locale.md)<br/>
[_free_locale](free-locale.md)<br/>
