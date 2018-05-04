---
title: strtoimax, _strtoimax_l —, wcstoimax —, _wcstoimax_l — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- wcstoimax
- _wcstoimax_l
- _strtoimax_l
- strtoimax
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
- wcstoimax
- _tcstoimax
- strtoimax
- _wcstoimax_l
- _strtoimax_l
- _tcstoimax_l
dev_langs:
- C++
helpviewer_keywords:
- strtoimax funciton
- conversion functions
- _strtoimax_l function
- _wcstoimax_l function
- wcstoimax function
ms.assetid: 4530d3dc-aaac-4a76-b7cf-29ae3c98d0ae
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 58ee8f4cbceaa2972de9a40a4192b1175b25488d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="strtoimax-strtoimaxl-wcstoimax-wcstoimaxl"></a>strtoimax, _strtoimax_l, wcstoimax, _wcstoimax_l

Konwertuje ciąg na wartość całkowitą typu największy obsługiwanych liczbę całkowitą ze znakiem.

## <a name="syntax"></a>Składnia

```C
intmax_t strtoimax(
   const char *strSource,
   char **endptr,
   int base
);
intmax_t wcstoimax(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base
);
intmax_t _strtoimax_l(
   const char *strSource,
   char **endptr,
   int base,
   _locale_t locale
);
intmax_t _wcstoimax_l(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*strSource*<br/>
Zerem ciąg do konwersji.

*endptr*<br/>
Wskaźnik do znaku, który zatrzymuje skanowania.

*base*<br/>
Podstawowy numer do użycia.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

**strtoimax** zwraca wartość, która jest reprezentowana w ciągu *strSource*, z wyjątkiem przypadków, gdy reprezentacja mogłoby spowodować przepełnienie — w takim przypadku zwraca **INTMAX_MAX** lub **INTMAX_MIN**, i **errno** ustawiono **erange —**. Funkcja zwraca wartość 0, jeśli konwersja nie jest możliwe. **wcstoimax —** zwraca wartości analogously do **strtoimax**.

**INTMAX_MAX** i **INTMAX_MIN** są zdefiniowane w stdint.h.

Jeśli *strSource* jest **NULL** lub *podstawowej* jest różna od zera i mniejszym niż 2 lub większą niż 36 **errno** ustawiono **einval —** .

Aby uzyskać więcej informacji na temat kody powrotu, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**Strtoimax** funkcji konwertuje *strSource* do **intmax_t**. Wersja znaków dwubajtowych **strtoimax** jest **wcstoimax —**; *strSource* argument jest ciąg znaków dwubajtowych. W przeciwnym razie funkcje te działają tak samo. Zatrzymaj funkcjami odczytywania ciąg *strSource* pierwszego znaku, ich nie jest rozpoznawana jako część liczby. Może to być znak końcowy null lub być może jest ona pierwszego znaku liczbowego, który jest większa niż lub równa *podstawowej*.

Ustawienia regionalne **lc_numeric —** ustawienie kategorii określa rozpoznawania po znaku radix *strSource*; Aby uzyskać więcej informacji, zobacz [setlocale, _wsetlocale —](setlocale-wsetlocale.md). Funkcje, które nie mają **_l** sufiks Użyj bieżących ustawień regionalnych; **_strtoimax_l —** i **_wcstoimax_l —** są takie same jak odpowiednie funkcje, które nie mają **_l** sufiks z tą różnicą, że zamiast tego użyć ustawienia regionalne to jest Przekazano. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

Jeśli *endptr* nie jest **NULL**, wskaźnik do znaku zatrzymania skanowania są przechowywane w lokalizacji, która jest wskazywana przez *endptr*. Jeśli konwersja nie można wykonać (nie znaleziono żadnych prawidłowych cyfr lub określono nieprawidłowy atrybut podstawowy), wartość *strSource* są przechowywane w lokalizacji, która jest wskazywana przez *endptr*.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoimax**|**strtoimax**|**strtoimax**|**wcstoimax**|
|**_tcstoimax_l**|**strtoimax_l**|**_strtoimax_l**|**_wcstoimax_l**|

**strtoimax** oczekuje *strSource* wskaż ciąg następującą postać:

> [*odstępem*] [{**+** &#124; **-**}] [**0** [{ **x** &#124; **X** }]] [*cyfr* &#124; *litery*]  

A *odstępem* może zawierać znaków miejsca i karty, które są ignorowane. *cyfr* są co najmniej jeden cyfr dziesiętnych; *litery* to jeden lub więcej litery "" do "z" (lub "A" do "Z"). Pierwszy znak należący do tego formularza zatrzymuje skanowania. Jeśli *podstawowej* jest od 2 do 36, zostanie użyty jako podstawa liczby. Jeśli *podstawowej* ma wartość 0, znaków ciągu wskazywana przez *strSource* są używane do określenia podstawy. Jeśli pierwszym znakiem "0" i nie jest znak "x" lub "X", ciąg jest interpretowany jako ósemkową liczby całkowitej. Jeśli pierwszym znakiem jest "0" i jest znak "x" lub "X", ciąg jest interpretowany jako szesnastkową liczby całkowitej. Jeśli pierwszym znakiem jest "1" do "9", ciąg jest interpretowany jako dziesiętną liczbą całkowitą. Litery "" do "z" (lub "" do "Z") mają przypisane wartości 10 do 35; tylko litery, w których przypisane wartości są mniej niż *podstawowej* są dozwolone. Pierwszy znak poza zakresem podstawy zatrzymuje skanowania. Na przykład jeśli *podstawowej* wynosi 0 i pierwszy znak skanowane to "0", zakłada, że całkowitą ósemkowe i się od znaku "8" lub "9" spowoduje zatrzymanie skanowania.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**strtoimax**, **_strtoimax_l —**, **wcstoimax —**, **_wcstoimax_l —**|\<inttypes.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[Konwertowanie ciągów na wartości](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtol, wcstol, _strtol_l, _wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[strtoumax, _strtoumax_l, wcstoumax, _wcstoumax_l](strtoumax-strtoumax-l-wcstoumax-wcstoumax-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
