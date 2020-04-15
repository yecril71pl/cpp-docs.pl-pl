---
title: strtol, wcstol, _strtol_l, _wcstol_l
ms.date: 4/2/2020
api_name:
- strtol
- wcstol
- _strtol_l
- _wcstol_l
- _o__strtol_l
- _o__wcstol_l
- _o_strtol
- _o_wcstol
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
- _wcstol_l
- strtol
- _tcstol
- wcstol
- _strtol_l
- _tcstol_l
helpviewer_keywords:
- wcstol function
- wcstol_l function
- _tcstol function
- string conversion, to integers
- tcstol function
- strtol_l function
- _wcstol_l function
- _strtol_l function
- strtol function
ms.assetid: 1787c96a-f283-4a83-9325-33cfc1c7e240
no-loc:
- strtol
- wcstol
- _strtol_l
- _wcstol_l
- LONG_MAX
- LONG_MIN
- errno
- ERANGE
- EINVAL
- LC_NUMERIC
- _tcstol
- _tcstol_l
- localeconv
- setlocale
- _wsetlocale
- strtod
- _strtod_l
- wcstod
- _wcstod_l
- strtoll
- _strtoll_l
- wcstoll
- _wcstoll_l
- strtoul
- _strtoul_l
- wcstoul
- _wcstoul_l
- atof
- _atof_l
- _wtof
- _wtof_l
ms.openlocfilehash: dbeaf04d34aa20e15de48e99082ed07edb6129ab
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320474"
---
# <a name="strtol-wcstol-_strtol_l-_wcstol_l"></a>strtol, wcstol, _strtol_l, _wcstol_l

Konwertuj ciągi na **długą** wartość całkowitą.

## <a name="syntax"></a>Składnia

```C
long strtol(
   const char *string,
   char **end_ptr,
   int base
);
long wcstol(
   const wchar_t *string,
   wchar_t **end_ptr,
   int base
);
long _strtol_l(
   const char *string,
   char **end_ptr,
   int base,
   _locale_t locale
);
long _wcstol_l(
   const wchar_t *string,
   wchar_t **end_ptr,
   int base,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*Ciąg*\
Ciąg zakończony wartością null do konwersji.

*end_ptr*\
Parametr wyjściowy, ustawiony na punkt znaku po ostatnim interpretowanym znaku. Ignorowane, jeśli **NULL**.

*Podstawowej*\
Podstawa liczbowa do użycia.

*Ustawień regionalnych*\
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

**strtol**, **wcstol**, **_strtol_l**i **_wcstol_l** zwracają wartość reprezentowaną w *ciągu*. Zwracają 0, jeśli konwersja nie jest możliwa. Gdy reprezentacja spowoduje przepełnienie, zwracają **LONG_MAX** lub **LONG_MIN**.

**errno** jest ustawiona na **ERANGE,** jeśli wystąpi przepełnienie lub niedopełnienie. Jest ustawiona na **Wartość EINVAL,** jeśli *ciąg* ma **wartość NULL**. Lub, jeśli *podstawa* jest niezerowa i mniejsza niż 2 lub większa niż 36. Aby uzyskać więcej informacji na temat **ERANGE,** **EINVAL**i innych kodów zwrotnych, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Funkcje **strtol**, **wcstol**, **_strtol_l**i **_wcstol_l** konwertuje *ciąg* na **długi.** Przestają czytać *ciąg* przy pierwszym znaku nie rozpoznawanym jako część liczby. Może to być znak kończący-null lub pierwszy znak alfanumeryczny większy niż lub równy *podstawie.*

**wcstol** i **_wcstol_l** są szerokoznakowymi wersjami **strtol** i **_strtol_l**. Ich argument *ciąg* jest ciągiem znaków o szerokim charakterze. Funkcje te zachowują się identycznie jak **strtol** i **_strtol_l** w przeciwnym razie. Ustawienie **kategorii LC_NUMERIC** ustawień regionalnych określa rozpoznawanie znaku radix (znacznika ułamkowego lub dziesiętnego) w *ciągu*. Funkcje **strtol** i **wcstol** używają bieżących ustawień regionalnych. **_strtol_l** i **_wcstol_l** użyć ustawień regionalnych przekazanych zamiast. Aby uzyskać więcej informacji, zobacz [setlocale] i [Ustawienia regionalne](../../c-runtime-library/locale.md).

Gdy *end_ptr* ma **wartość NULL**, jest ignorowana. W przeciwnym razie wskaźnik do znaku, który zatrzymał skanowanie jest przechowywany w miejscu wskazanym przez *end_ptr*. Konwersja nie jest możliwa, jeśli nie zostaną znalezione prawidłowe cyfry lub określono nieprawidłową bazę. Wartość *ciągu* jest następnie przechowywana w miejscu wskazanym przez *end_ptr*.

**strtol** *oczekuje,* że ciąg wskazuje ciąg następującego formularza:

> [*odstępy*] [{**+** &#124; **-**}] [**0** [{ **x** &#124; **X** }]] [*alfanumeryczna*]

Nawiasy kwadratowe (`[ ]`) otaczają elementy opcjonalne. Nawiasy klamrowe i pionowy pasek (`{ | }`) otaczają alternatywy dla pojedynczego elementu. *odstępy* mogą składać się ze znaków spacji i tabulacji, które są ignorowane. *alfanumeryczne* są cyframi dziesiętnymi lub literami "a" przez "z" (lub "A" do "Z"). Pierwszy znak, który nie pasuje do tego formularza, zatrzymuje skanowanie. Jeśli *podstawa* znajduje się między 2 a 36, jest używana jako podstawa liczby. Jeśli *podstawa* wynosi 0, początkowe znaki ciągu wskazywu przez *ciąg* są używane do określenia podstawy. Jeśli pierwszy znak ma 0, a drugi znak nie jest "x" lub "X", ciąg jest interpretowany jako ósemkowa liczba całkowita. Jeśli pierwszy znak to "0", a drugi znak to "x" lub "X", ciąg jest interpretowany jako liczba całkowita szesnastkowa. Jeśli pierwszy znak jest od 1 do "9", ciąg jest interpretowany jako liczba całkowita dziesiętna. Literom "a" do "z" (lub "A" do "Z") przypisuje się wartości od 10 do 35. Skanowanie zezwala tylko na litery, których wartości są mniejsze niż *podstawowe*. Pierwszy znak poza zakresem podstawy zatrzymuje skanowanie. Załóżmy na przykład, że *ciąg* zaczyna się od "01". Jeśli *podstawa* wynosi 0, skaner zakłada, że jest to ósemka całkowita. Znak "8" lub "9" zatrzymuje skanowanie.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstol**|**strtol (strtol)**|**strtol (strtol)**|**wcstol**|
|**_tcstol_l**|**_strtol_l**|**_strtol_l**|**_wcstol_l**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**strtol**|\<>|
|**wcstol**|\<> lub \<wchar.h>|
|**_strtol_l**|\<>|
|**_wcstol_l**|\<> lub \<wchar.h>|

**_strtol_l** Funkcje **_wcstol_l** i funkcje są specyficzne dla firmy Microsoft, a nie częścią biblioteki Standard C. Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [strtod](strtod-strtod-l-wcstod-wcstod-l.md)dla .

## <a name="see-also"></a>Zobacz też

[Konwersja danych](../data-conversion.md)\
[Ustawień regionalnych](../locale.md)\
[localeconv](localeconv.md)\
[setlocale, _wsetlocale](setlocale-wsetlocale.md)\
[Ciąg do funkcji wartości liczbowej](../string-to-numeric-value-functions.md)\
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)\
[strtoll, _strtoll_l, wcstoll, _wcstoll_l](strtoll-strtoll-l-wcstoll-wcstoll-l.md)\
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)\
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)
