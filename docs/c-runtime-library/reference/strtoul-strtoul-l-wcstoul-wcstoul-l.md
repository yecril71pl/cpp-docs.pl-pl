---
title: strtoul, _strtoul_l, wcstoul, _wcstoul_l
ms.date: 4/2/2020
api_name:
- _wcstoul_l
- _strtoul_l
- strtoul
- wcstoul
- _o__strtoul_l
- _o__wcstoul_l
- _o_strtoul
- _o_wcstoul
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
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- strtoul
- _tcstoul
- wcstoul
helpviewer_keywords:
- _wcstoul_l function
- _tcstoul function
- _strtoul_l function
- string conversion, to integers
- wcstoul function
- strtoul function
- wcstoul_l function
- strtoul_l function
- tcstoul function
ms.assetid: 38f2afe8-8178-4e0b-8bbe-d5c6ad66e3ab
ms.openlocfilehash: 60ae432fb11c5a29da2c4830c2a85305c6eaa46c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365625"
---
# <a name="strtoul-_strtoul_l-wcstoul-_wcstoul_l"></a>strtoul, _strtoul_l, wcstoul, _wcstoul_l

Konwertuj ciągi na niepodpisaną wartość całkowitej.

## <a name="syntax"></a>Składnia

```C
unsigned long strtoul(
   const char *strSource,
   char **endptr,
   int base
);
unsigned long _strtoul_l(
   const char *strSource,
   char **endptr,
   int base,
   _locale_t locale
);
unsigned long wcstoul(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base
);
unsigned long _wcstoul_l(
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

**strtoul** zwraca przekonwertowane wartości, jeśli istnieje, lub **ULONG_MAX** na przepełnienie. **strtoul** zwraca wartość 0, jeśli nie można przeprowadzić konwersji. **wcstoul** zwraca wartości analogicznie do **strtoul**. Dla obu funkcji **errno** jest ustawiona na **ERANGE,** jeśli występuje przepełnienie lub niedopełnienie.

Zobacz [_doserrno, errno, _sys_errlist i _sys_nerr,](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) aby uzyskać więcej informacji na ten temat i inne kody zwrotne.

## <a name="remarks"></a>Uwagi

Każda z tych funkcji konwertuje ciąg wejściowy *strSource* na **niepodpisany** **długi**.

**strtoul** przestaje odczytywać ciąg *strSource* przy pierwszym znaku nie może rozpoznać jako część liczby. Może to być kończący się znak null lub pierwszy znak numeryczny większy lub równy *podstawie.* Ustawienie kategorii **LC_NUMERIC** ustawień regionalnych określa rozpoznawanie znaku radix w *strSource*; aby uzyskać więcej informacji, zobacz [setlocale](setlocale-wsetlocale.md). **strtoul** i **wcstoul** używać bieżących ustawień regionalnych; **_strtoul_l** i **_wcstoul_l** są identyczne, z tą różnicą, że zamiast tego używają ustawień regionalnych przekazanych. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

Jeśli *endptr* nie ma **wartości NULL,** wskaźnik do znaku, który zatrzymał skanowanie jest przechowywany w miejscu wskazanym przez *endptr*. Jeśli nie można przeprowadzić konwersji (nie znaleziono prawidłowych cyfr lub określono nieprawidłową bazę), wartość *strSource* jest przechowywana w lokalizacji wskazanej przez *endptr*.

**wcstoul** jest szerokoznakową wersją **strtoul;** jego *argument strSource* jest ciągiem znaków o szerokim charakterze. W przeciwnym razie te funkcje zachowują się identycznie.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoul**|**strtoul ( strtoul )**|**strtoul ( strtoul )**|**wcstoul ( wcstoul )**|
|**_tcstoul_l**|**strtoul_l**|**_strtoul_l**|**_wcstoul_l**|

**strtoul** oczekuje *strSource* wskazać ciąg następującej postaci:

> [*odstępy*] [{**+** &#124; **-**}] [**0** [{ **x** &#124; **X** }]] [*cyfry* &#124; *litery*]

*Odstępy* mogą składać się ze znaków spacji i tabulacji, które są ignorowane. *cyfry* są co najmniej jedną cyfrą dziesiętną. *litery* są jedną lub kilkoma literami "a" przez "z" (lub "A" do "Z"). Pierwszy znak, który nie pasuje do tego formularza, zatrzymuje skanowanie. Jeśli *podstawa* znajduje się między 2 a 36, jest używana jako podstawa liczby. Jeśli *podstawa* wynosi 0, początkowe znaki ciągu wskazywowane przez *strSource* są używane do określenia podstawy. Jeśli pierwszy znak ma 0, a drugi znak nie jest "x" lub "X", ciąg jest interpretowany jako ósemkowa liczba całkowita. Jeśli pierwszy znak to "0", a drugi znak to "x" lub "X", ciąg jest interpretowany jako liczba całkowita szesnastkowa. Jeśli pierwszy znak jest od 1 do "9", ciąg jest interpretowany jako liczba całkowita dziesiętna. Literom "a" do "z" (lub "A" do "Z") przypisuje się wartości od 10 do 35; tylko litery, których przypisane wartości są mniejsze niż *podstawy* są dozwolone. Pierwszy znak poza zakresem podstawy zatrzymuje skanowanie. Na przykład, jeśli *podstawa* wynosi 0, a pierwszy zeskanowany znak to "0", zakłada się ósemkową liczę całkowitą, a znak "8" lub "9" zatrzyma skanowanie. **strtoul** pozwala na**+** plus (**-**) lub minus ( ) prefiks znaku; wiodący znak minus wskazuje, że zwracana wartość jest negowana.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**strtoul ( strtoul )**|\<>|
|**wcstoul ( wcstoul )**|\<> lub \<wchar.h>|
|**_strtoul_l**|\<>|
|**_wcstoul_l**|\<> lub \<wchar.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [strtod](strtod-strtod-l-wcstod-wcstod-l.md).

## <a name="see-also"></a>Zobacz też

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Ustawienia regionalne](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[Ciąg do funkcji wartości liczbowej](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtol, wcstol, _strtol_l, _wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
