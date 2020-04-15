---
title: strtoll, _strtoll_l, wcstoll, _wcstoll_l
ms.date: 4/2/2020
api_name:
- strtoll
- wcstoll
- _strtoll_l
- _wcstoll_l
- _o__strtoll_l
- _o__wcstoll_l
- _o_strtoll
- _o_wcstoll
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
- _strtoll_l
- _tcstoll_l
- _tcstoll
- _wcstoll_l
- strtoll
- wcstoll
helpviewer_keywords:
- _tcstoll_l function
- _wcstoll_l function
- strtoll function
- wcstoll function
- _tcstoll function
- _strtoll_l function
ms.assetid: e2d05dcf-d3b2-4291-9e60-dee77e540fd7
ms.openlocfilehash: d5a0ce8cb2c1d5f88d5439b99047609b32c8d2ec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365177"
---
# <a name="strtoll-_strtoll_l-wcstoll-_wcstoll_l"></a>strtoll, _strtoll_l, wcstoll, _wcstoll_l

Konwertuje ciąg na **długą** **wartość.**

## <a name="syntax"></a>Składnia

```C
long long strtoll(
   const char *strSource,
   char **endptr,
   int base
);
long long wcstoll(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base
);
long long _strtoll_l(
   const char *strSource,
   char **endptr,
   int base,
   _locale_t locale
);
long long _wcstoll_l(
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

**strtoll** zwraca wartość, która jest reprezentowana w *strSource*ciągu , z wyjątkiem sytuacji, gdy reprezentacja może spowodować przepełnienie — w takim przypadku zwraca **LLONG_MAX** lub **LLONG_MIN**. Funkcja zwraca wartość 0, jeśli nie można wykonać konwersji. **wcstoll** zwraca wartości analogicznie do **strtoll**.

**LLONG_MAX** i **LLONG_MIN** są zdefiniowane w limitach. H.

Jeśli *strSource* ma **wartość NULL** lub *podstawa* jest niezerowa i mniejsza niż 2 lub większa niż 36, **errno** jest ustawiona na **wartość EINVAL**.

Aby uzyskać więcej informacji na temat kodów zwrotnych, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Funkcja **strtoll** konwertuje *strSource* na **długi** **długi**. Obie funkcje przestają odczytywać ciąg *strSource* przy pierwszym znaku, który nie może rozpoznać jako część liczby. Może to być kończący się znak null lub pierwszy znak numeryczny, który jest większy lub równy *podstawie.* **wcstoll** jest szerokoznakową wersją **strtoll;** jego *argument strSource* jest ciągiem znaków o szerokim charakterze. W przeciwnym razie te funkcje zachowują się identycznie.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoll**|**strtoll ( strtoll )**|**strtoll ( strtoll )**|**wcstoll**|
|**_tcstoll_l**|**_strtoll_l**|**_strtoll_l**|**_wcstoll_l**|

Ustawienie **kategorii LC_NUMERIC** ustawień regionalnych określa rozpoznawanie znaku radix w *strSource*; aby uzyskać więcej informacji, zobacz [setlocale, _wsetlocale](setlocale-wsetlocale.md). Funkcje, które nie mają sufiksu **_l,** używają bieżących ustawień regionalnych; **_strtoll_l** i **_wcstoll_l** są identyczne z odpowiednimi funkcjami, które nie mają sufiksu, z tą różnicą, że zamiast tego używają ustawień regionalnych, które są przekazywane. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

Jeśli *endptr* nie jest **null**, wskaźnik do znaku, który zatrzymał skanowanie jest przechowywany w miejscu, które jest wskazywane przez *endptr*. Jeśli nie można przeprowadzić konwersji (nie znaleziono prawidłowych cyfr lub określono nieprawidłową bazę), wartość *strSource* jest przechowywana w lokalizacji wskazanej przez *endptr*.

**strtoll** oczekuje *strSource* wskazać ciąg następującej postaci:

> [*odstępy*] [{**+** &#124; **-**}] [**0** [{ **x** &#124; **X** }]] [*cyfry* &#124; *litery*]

*Odstępy* mogą składać się ze znaków spacji i tabulacji, które są ignorowane; *cyfry* są jedną lub kilkoma cyframi dziesiętnymi; *litery* są jedną lub kilkoma literami "a" przez "z" (lub "A" do "Z"). Pierwszy znak, który nie pasuje do tego formularza, zatrzymuje skanowanie. Jeśli *podstawa* znajduje się między 2 a 36, jest używana jako podstawa liczby. Jeśli *baza* wynosi 0, początkowe znaki ciągu, który jest wskazyny przez *strSource* są używane do określenia bazy. Jeśli pierwszy znak to "0", a drugi znak nie jest "x" lub "X", ciąg jest interpretowany jako ósemkowa liczba całkowita. Jeśli pierwszy znak to "0", a drugi znak to "x" lub "X", ciąg jest interpretowany jako liczba całkowita szesnastkowa. Jeśli pierwszy znak jest od 1 do "9", ciąg jest interpretowany jako liczba całkowita dziesiętna. Literom "a" do "z" (lub "A" do "Z") przypisuje się wartości od 10 do 35; tylko litery, których przypisane wartości są mniejsze niż *podstawy* są dozwolone. Pierwszy znak poza zakresem podstawy zatrzymuje skanowanie. Na przykład, jeśli *podstawa* wynosi 0, a pierwszy zeskanowany znak to "0", zakłada się ósemkową ćgiętę całkowitą, a znak "8" lub "9" zatrzymuje skanowanie.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**strtoll**, **_strtoll_l**|\<>|
|**wcstoll**, **_wcstoll_l**|\<> lub \<wchar.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Ustawienia regionalne](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[Ciąg do funkcji wartości liczbowej](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtol, wcstol, _strtol_l, _wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
