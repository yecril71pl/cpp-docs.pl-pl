---
title: strtold, _strtold_l, wcstold, _wcstold_l | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
ms.assetid: 928c0c9a-bc49-445b-8822-100eb5954115
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4d73a554066ed5a5e25fd0d46d948b01af0c621c
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="strtold-strtoldl-wcstold-wcstoldl"></a>strtold, _strtold_l, wcstold, _wcstold_l

Konwertuje ciągów na wartości zmiennoprzecinkowej długo podwójnej precyzji.

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
Zerem ciąg do konwersji.

*endptr*<br/>
Wskaźnik do znaku, który zatrzymuje skanowania.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

**strtold** zwraca wartość liczby zmiennoprzecinkowej jako **długi** **podwójne**, z wyjątkiem przypadków, gdy reprezentacja mogłoby spowodować przepełnienie — w takim przypadku funkcja zwraca +/-**HUGE_VALL**. Znak **HUGE_VALL** znak wartość, która nie może być przedstawiony jest zgodna. **strtold** zwraca wartość 0, jeśli konwersja nie można wykonać lub niedopełnienie występuje.

**wcstold** zwraca wartości analogously do **strtold**. Dla obu tych funkcji **errno** ustawiono **erange —** Jeśli występuje przepełnienie lub niedomiar i program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md).

Aby uzyskać więcej informacji na temat kody powrotu, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Funkcja każdego konwertuje ciąg wejściowy *strSource* do **długi** **podwójne**. **Strtold** funkcja przestaje czytać ciąg *strSource* pierwszego znaku nie jest rozpoznawana jako część liczby. Może to być znak końcowy null. Wersja znaków dwubajtowych **strtold** jest **wcstold**; *strSource* argument jest ciąg znaków dwubajtowych. W przeciwnym razie funkcje te działają tak samo.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstold**|**strtold**|**strtold**|**wcstold**|
|**_tcstold_l**|**_strtold_l**|**_strtold_l**|**_wcstold_l**|

**Lc_numeric —** ustawienie kategorii bieżące ustawienia regionalne określa rozpoznawania znaku podstawa w *strSource*. Aby uzyskać więcej informacji, zobacz [setlocale, _wsetlocale —](setlocale-wsetlocale.md). Funkcje bez **_l** sufiks Użyj bieżących ustawień regionalnych; **_strtold_l** i **_wcstold_l** są takie same jak **_strtold** i **_wcstold** z tą różnicą, że zamiast tego użyć ustawienia regionalne to jest Przekazano. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

Jeśli *endptr* nie jest **NULL**, wskaźnik do znaku zatrzymania skanowania są przechowywane w lokalizacji, która jest wskazywana przez *endptr*. Jeśli konwersja nie można wykonać (nie znaleziono żadnych prawidłowych cyfr lub określono nieprawidłowy atrybut podstawowy), wartość *strSource* są przechowywane w lokalizacji, która jest wskazywana przez *endptr*.

**strtold** oczekuje *strSource* wskaż ciąg następującą postać:

[*odstępem*] [*znak*] [*cyfr*] [. *cyfry*] [{**d** &#124; **D** &#124; **e** &#124; **E**} [*logowania* ]*cyfr*]

A *odstępem* może zawierać znaków miejsca i karty, które są ignorowane. *znak* jest plus (**+**) lub minus (**-**); i *cyfr* są co najmniej jeden cyfr dziesiętnych. Jeśli cyfr nie pojawia się przed znakiem podstawa, co najmniej jeden musi występować po znaku podstawę systemu liczbowego. Wykładnik, obejmującego wprowadzające litery może zawierać wyłącznie cyfr dziesiętnych (**d**, **D**, **e**, lub **E**) i opcjonalnie liczbę całkowitą ze znakiem. Jeśli pojawi się części wykładnika ani znaków podstawa, znak radix — zakłada się, że wykonaj ostatnich cyfr w ciągu. Pierwszy znak należący do tego formularza zatrzymuje skanowania.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**strtold**, **_strtold_l**|\<stdlib.h>|
|**wcstold**, **_wcstold_l**|\<stdlib.h > lub \<wchar.h >|

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
