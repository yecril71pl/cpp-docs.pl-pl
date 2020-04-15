---
title: _strtoi64, _wcstoi64, _strtoi64_l, _wcstoi64_l
ms.date: 4/2/2020
api_name:
- _strtoi64
- _strtoi64_l
- _wcstoi64_l
- _wcstoi64
- _o__strtoi64
- _o__strtoi64_l
- _o__wcstoi64
- _o__wcstoi64_l
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
- _strtoi64
- strtoi64
- _stroi64_l
- _wcstoi64_l
- wcstoi64_l
- _wcstoi64
- wcstoi64
- strtoi64_l
helpviewer_keywords:
- _strtoi64 function
- _wcstoi64 function
- _strtoi64_l function
- string conversion, to integers
- _wcstoi64_l function
- strtoi64_l function
- wcstoi64 function
- strtoi64 function
- wcstoi64_l function
ms.assetid: ea2abc50-7bfe-420e-a46b-703c3153593a
ms.openlocfilehash: 8dcdff4cf6f3eff191dc126583c1ca8290133e02
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365130"
---
# <a name="_strtoi64-_wcstoi64-_strtoi64_l-_wcstoi64_l"></a>_strtoi64, _wcstoi64, _strtoi64_l, _wcstoi64_l

Konwertowanie ciągu na wartość **__int64.**

## <a name="syntax"></a>Składnia

```C
__int64 _strtoi64(
   const char *strSource,
   char **endptr,
   int base
);
__int64 _wcstoi64(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base
);
__int64 _strtoi64_l(
   const char *strSource,
   char **endptr,
   int base,
   _locale_t locale
);
__int64 _wcstoi64_l(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*strSource (źródło usług strSource)*<br/>
Ciąg zakończony wartością null do konwersji.

*endptr*<br/>
Wskaźnik do znaku, który zatrzymuje skanowanie.

*base*<br/>
Podstawa liczbowa do użycia.

*Ustawień regionalnych*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

**_strtoi64** zwraca wartość reprezentowaną w ciągu *strSource*, z wyjątkiem sytuacji, gdy reprezentacja spowoduje przepełnienie, w którym to przypadku zwraca **_I64_MAX** lub **_I64_MIN**. Funkcja zwróci wartość 0, jeśli nie można wykonać konwersji. **_wcstoi64** zwraca wartości analogicznie do **strtoi64**.

**_I64_MAX** i **_I64_MIN** są zdefiniowane w limitach. H.

Jeśli *strSource* ma **wartość NULL** lub *podstawa* jest niezerowa i mniejsza niż 2 lub większa niż 36, **errno** jest ustawiona na **wartość EINVAL**.

Zobacz [_doserrno, errno, _sys_errlist i _sys_nerr,](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) aby uzyskać więcej informacji na temat tych i innych kodów zwrotnych.

## <a name="remarks"></a>Uwagi

Funkcja **_strtoi64** konwertuje *strSource* na **__int64**. Obie funkcje przestają odczytywać ciąg *strSource* przy pierwszym znaku, który nie może rozpoznać jako część liczby. Może to być kończący się znak null lub pierwszy znak numeryczny większy lub równy *podstawie.* **_wcstoi64** jest szerokoznakową wersją **_strtoi64**; jego *argument strSource* jest ciągiem znaków o szerokim charakterze. Te funkcje zachowują się identycznie w przeciwnym razie.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoi64**|**_strtoi64**|**_strtoi64**|**_wcstoi64**|
|**_tcstoi64_l**|**_strtoi64_l**|**_strtoi64_l**|**_wcstoi64_l**|

Ustawienie **kategorii LC_NUMERIC** ustawień regionalnych określa rozpoznawanie znaku radix w *strSource*; aby uzyskać więcej informacji, zobacz [setlocale](setlocale-wsetlocale.md). Funkcje bez sufiksu _l używają bieżących ustawień regionalnych; **_strtoi64_l** i **_wcstoi64_l** są identyczne z odpowiednią funkcją bez sufiksu **_l,** z tą różnicą, że zamiast tego używają ustawień regionalnych przekazanych. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

Jeśli *endptr* nie ma **wartości NULL,** wskaźnik do znaku, który zatrzymał skanowanie jest przechowywany w miejscu wskazanym przez *endptr*. Jeśli nie można przeprowadzić konwersji (nie znaleziono prawidłowych cyfr lub określono nieprawidłową bazę), wartość *strSource* jest przechowywana w lokalizacji wskazanej przez *endptr*.

**_strtoi64** oczekuje *strSource* wskazać ciąg następującego formularza:

> [*odstępy*] [{**+** &#124; **-**}] [**0** [{ **x** &#124; **X** }]] [*cyfry* &#124; *litery*]

*Odstępy* mogą składać się ze znaków spacji i tabulacji, które są ignorowane; *cyfry* są jedną lub kilkoma cyframi dziesiętnymi; *litery* są jedną lub kilkoma literami "a" przez "z" (lub "A" do "Z").  Pierwszy znak, który nie pasuje do tego formularza, zatrzymuje skanowanie. Jeśli *podstawa* znajduje się między 2 a 36, jest używana jako podstawa liczby. Jeśli *podstawa* wynosi 0, początkowe znaki ciągu wskazywowane przez *strSource* są używane do określenia podstawy. Jeśli pierwszy znak ma 0, a drugi znak nie jest "x" lub "X", ciąg jest interpretowany jako ósemkowa liczba całkowita. Jeśli pierwszy znak to "0", a drugi znak to "x" lub "X", ciąg jest interpretowany jako liczba całkowita szesnastkowa. Jeśli pierwszy znak jest od 1 do "9", ciąg jest interpretowany jako liczba całkowita dziesiętna. Literom "a" do "z" (lub "A" do "Z") przypisuje się wartości od 10 do 35; tylko litery, których przypisane wartości są mniejsze niż *podstawy* są dozwolone. Pierwszy znak poza zakresem podstawy zatrzymuje skanowanie. Na przykład, jeśli *podstawa* wynosi 0, a pierwszy zeskanowany znak to "0", zakłada się ósemkową liczę całkowitą, a znak "8" lub "9" zatrzyma skanowanie.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_strtoi64** **, _strtoi64_l**|\<>|
|**_wcstoi64** **, _wcstoi64_l**|\<> lub \<wchar.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Ustawienia regionalne](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[Ciąg do funkcji wartości liczbowej](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
