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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: ba57eed25fd8e1310b9e837c55cb1e1f7ec2b718
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82912601"
---
# <a name="strtold-_strtold_l-wcstold-_wcstold_l"></a>strtold, _strtold_l, wcstold, _wcstold_l

Konwertuje ciągi na wartość Long-zmiennoprzecinkową o podwójnej precyzji.

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
Ciąg zakończony znakiem null do przekonwertowania.

*endptr*<br/>
Wskaźnik do znaku, który zatrzyma skanowanie.

*locale*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

**strtold** zwraca wartość liczby zmiennoprzecinkowej jako **długą** **podwójną**, z wyjątkiem sytuacji, gdy reprezentacja spowodowałaby przepełnienie — w takim przypadku funkcja zwraca wartość +/-**HUGE_VALL**. Znak **HUGE_VALL** jest zgodny ze znakiem wartości, która nie może być reprezentowana. **strtold** zwraca wartość 0, jeśli nie można wykonać konwersji lub występuje niedopełnienie.

**wcstold** zwraca wartości analogicznie do **strtold**. W przypadku obu funkcji **errno** jest ustawiony na **ERANGE** , jeśli występuje przepełnienie lub nadmiarowy i zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md).

Aby uzyskać więcej informacji na temat kodów powrotnych, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Każda funkcja konwertuje ciąg wejściowy *strSource* na **Long** **Double**. Funkcja **strtold** przestaje odczytywania ciągu *strSource* przy pierwszym znaku, którego nie może rozpoznać jako części liczby. Może to być kończący znak null. Dwubajtowa wersja **strtold** jest **wcstold**; jego argument *strSource* jest ciągiem znaków dwubajtowych. W przeciwnym razie funkcje te zachowują się identycznie.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _MBCS _UNICODE &|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstold**|**strtold**|**strtold**|**wcstold**|
|**_tcstold_l**|**_strtold_l**|**_strtold_l**|**_wcstold_l**|

Ustawienie kategorii **LC_NUMERIC** bieżących ustawień regionalnych określa rozpoznawanie znaku podstawy w *strSource*. Aby uzyskać więcej informacji, zobacz [setlocals, _wsetlocale](setlocale-wsetlocale.md). Funkcje bez sufiksu **_l** używają bieżących ustawień regionalnych; **_strtold_l** i **_wcstold_l** są takie same jak **_strtold** i **_wcstold** , z tą różnicą, że zamiast nich używają ustawień regionalnych, które są przesyłane. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

Jeśli *endptr* nie ma **wartości null**, wskaźnik do znaku, który zatrzymał skanowanie jest przechowywany w lokalizacji wskazywanej przez *endptr*. Jeśli konwersja nie może być wykonywana (nie znaleziono prawidłowych cyfr lub określono nieprawidłową podstawę), wartość *strSource* jest przechowywana w lokalizacji wskazywanej przez *endptr*.

**strtold** oczekuje, że *strSource* wskazuje ciąg o następującej postaci:

[*odstęp*] [*Sign*] [*cyfry*] [. *cyfry*] [{**d** &#124; **d** &#124; **e** &#124; **e**} [*Sign*]*cyfr*]

*Odstępy* mogą składać się ze znaków spacji i tabulatora, które są ignorowane; *znak* jest znakiem plus**+**() lub minus**-**(); i *cyfry* są jedną lub większą liczbą cyfr dziesiętnych. Jeśli żadne cyfry nie pojawiają się przed znakiem podstawy, co najmniej jeden musi występować po znaku podstawy. Po cyfrach dziesiętnych można stosować wykładnikę, która składa się z litery wprowadzającej (**d**, **d**, **e**lub **e**) i opcjonalnie podpisanej liczby całkowitej. Jeśli nie zostanie wyświetlona żadna część wykładnika ani znak podstawy, przyjmuje się, że znak podstawy będzie podążać za ostatnią cyfrą w ciągu. Pierwszy znak, który nie pasuje do tego formularza, zatrzyma skanowanie.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**strtold**, **_strtold_l**|\<STDLIB. h>|
|**wcstold**, **_wcstold_l**|\<STDLIB. h> lub \<WCHAR. h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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
[Obsługa zmiennoprzecinkowa](../../c-runtime-library/floating-point-support.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[Ustawienie](../../c-runtime-library/locale.md)<br/>
[Funkcje ciągu do wartości numerycznych](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtol, wcstol, _strtol_l, _wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[localeconv](localeconv.md)<br/>
[_create_locale, _wcreate_locale](create-locale-wcreate-locale.md)<br/>
[_free_locale](free-locale.md)<br/>
