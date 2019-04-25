---
title: _strtoi64, _wcstoi64, _strtoi64_l, _wcstoi64_l
ms.date: 11/04/2016
apiname:
- _strtoi64
- _strtoi64_l
- _wcstoi64_l
- _wcstoi64
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
ms.openlocfilehash: b5479448a4e3a3cedba3a62d9b12b0dbe4160f7c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62176177"
---
# <a name="strtoi64-wcstoi64-strtoi64l-wcstoi64l"></a>_strtoi64, _wcstoi64, _strtoi64_l, _wcstoi64_l

Konwertuj ciąg na **__int64** wartości.

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

*strSource*<br/>
Ciąg zakończony wartością null do konwersji.

*endptr*<br/>
Wskaźnik znaku zatrzymującego skanowanie.

*base*<br/>
Numer podstawowy do użycia.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

**_strtoi64 —** zwraca wartość reprezentowana w ciągu *strSource*, gdy ta reprezentacja spowodowałoby przepełnienie, z wyjątkiem przypadków, jego zwraca **_I64_MAX** lub **_I64 _MIN**. Funkcja zwróci wartość 0, jeśli nie można wykonać konwersji. **_wcstoi64 —** zwraca wartości analogicznie do **strtoi64 —**.

**_I64_MAX** i **_I64_MIN** są zdefiniowane w granicach. H.

Jeśli *strSource* jest **NULL** lub *podstawowy* jest różna od zera i albo mniejszy niż 2 albo większy niż 36, atrybut **errno** ustawiono **EINVAL** .

Zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) kody powrotne — Aby uzyskać więcej informacji na temat tych i innych.

## <a name="remarks"></a>Uwagi

**_Strtoi64 —** funkcji konwertuje *strSource* do **__int64**. Obie funkcje przestają odczytywać ciąg *strSource* przy pierwszym znaku, ich nie może rozpoznać jako elementu liczby. Może to być kończący znak null lub pierwszy znak numeryczny, większa niż lub równa może być *podstawowy*. **_wcstoi64 —** to wersja znaku dwubajtowego **_strtoi64 —**; jej *strSource* argumentu jest ciągiem znaku dwubajtowego. Funkcje te zachowują się identycznie.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoi64**|**_strtoi64**|**_strtoi64**|**_wcstoi64**|
|**_tcstoi64_l**|**_strtoi64_l**|**_strtoi64_l**|**_wcstoi64_l**|

Ustawienia regionalne **LC_NUMERIC** ustawienie kategorii określa rozpoznawanie znaku podstawy w parametrze *strSource*; Aby uzyskać więcej informacji, zobacz [setlocale](setlocale-wsetlocale.md). Funkcje, które mają przyrostka _l używają bieżących ustawień regionalnych; **_strtoi64_l —** i **_wcstoi64_l —** są identyczne z odpowiednimi funkcjami bez **_l** sufiks z tą różnicą, że używają w zamian przekazanych ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

Jeśli *endptr* nie **NULL**, wskaźnik znaku, który zatrzymał skanowanie jest przechowywany w lokalizacji wskazywanej przez *endptr*. Jeśli konwersja nie może być wykonywana (nie znaleziono żadnych prawidłowych cyfr lub określono nieprawidłową podstawę), wartość *strSource* jest przechowywany w lokalizacji wskazywanej przez *endptr*.

**_strtoi64 —** oczekuje *strSource* do wskaże ciąg o następującej postaci:

> [*odstępu*] [{**+** &#124; **-**}] [**0** [{ **x** &#124; **X** }]] [*cyfr* &#124; *litery*]  

A *odstępu* może składać się ze znaków spacji lub tabulatora, które są ignorowane. *cyfr* są co najmniej jedna cyfra dziesiętna; *litery* są co najmniej liter "" do "z" (lub "A" do "Z").  Pierwszy znak, który nie mieści się tym formularzu zatrzymuje skanowanie. Jeśli *podstawowy* jest między 2 a 36, zostanie użyty jako podstawa numeru. Jeśli *podstawowy* ma wartość 0, początkowe znaki ciągu wskazywany przez *strSource* są używane do określenia podstawy. Jeśli pierwszym znakiem jest 0, a drugim znakiem nie jest,, x"lub,, X", ciąg jest interpretowany jako ósemkowa liczba całkowita. Jeśli pierwszym znakiem jest "0", a drugim znakiem jest,, x"lub,, X", ciąg jest interpretowany jako szesnastkowa liczba całkowita. Jeśli pierwszym znakiem jest,, 1 "do,, 9", ciąg jest interpretowany jako dziesiętna liczba całkowita. Litery od "" do "z" (lub "" – "Z") są przypisane wartości od 10 do 35; tylko litery, w których przypisane wartości są mniej niż *podstawowy* są dozwolone. Pierwszy znak spoza zakresu podstawy zatrzymuje skanowanie. Na przykład jeśli *podstawowy* wynosi 0 i pierwszy znak skanowany to "0", zakłada, że ósemkowa liczba całkowitej i znaku "8" lub "9" zatrzyma skanowanie.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_strtoi64**, **_strtoi64_l**|\<stdlib.h>|
|**_wcstoi64**, **_wcstoi64_l**|\<stdlib.h> or \<wchar.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[Konwertowanie ciągów na wartości](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
