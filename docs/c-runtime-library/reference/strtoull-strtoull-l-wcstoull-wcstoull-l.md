---
title: strtoull, _strtoull_l, wcstoull, _wcstoull_l
ms.date: 4/2/2020
api_name:
- _strtoull_l
- _wcstoull_l
- strtoull
- wcstoull
- _o__strtoull_l
- _o__wcstoull_l
- _o_strtoull
- _o_wcstoull
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
- _wcstoull_l
- _tcstoull
- _tcstoull_l
- wcstoull
- _strtoull_l
- strtoull
helpviewer_keywords:
- strtoull function
- _tcstoull_l function
- _tcstoull function
- _wcstoull_l function
- _strtoull_l function
- wcstoull function
ms.assetid: 36dac1cc-e901-40a0-8802-63562d6d01df
ms.openlocfilehash: 5a27218b9d83314f995df30fbe21d97031d371af
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354052"
---
# <a name="strtoull-_strtoull_l-wcstoull-_wcstoull_l"></a>strtoull, _strtoull_l, wcstoull, _wcstoull_l

Konwertuje ciągi na niepodpisaną długą wartość całkowitą.

## <a name="syntax"></a>Składnia

```C
unsigned long long strtoull(
   const char *strSource,
   char **endptr,
   int base
);
unsigned long long _strtoull_l(
   const char *strSource,
   char **endptr,
   int base,
   _locale_t locale
);
unsigned long long wcstoull(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base
);
unsigned long long _wcstoull_l(
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

**strtoull** zwraca przekonwertowane wartości, jeśli istnieje, lub **ULLONG_MAX** na przepełnienie. **strtoull** zwraca wartość 0, jeśli nie można przeprowadzić konwersji. **wcstoull** zwraca wartości analogicznie do **strtoull**. Dla obu funkcji **errno** jest ustawiona na **ERANGE,** jeśli występuje przepełnienie lub niedopełnienie.

Aby uzyskać więcej informacji na temat kodów zwrotnych, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Każda z tych funkcji konwertuje ciąg wejściowy *strSource* na **niepodpisaną** **długą** **long** wartość całkowitą.

**strtoull** przestaje odczytywać ciąg *strSource* przy pierwszym znaku nie może rozpoznać jako część liczby. Może to być kończący się znak null lub pierwszy znak numeryczny, który jest większy lub równy *podstawie.* Ustawienie **LC_NUMERIC** kategorii ustawień regionalnych określa rozpoznawanie znaku radix w *strSource*; aby uzyskać więcej informacji, zobacz [setlocale, _wsetlocale](setlocale-wsetlocale.md). **strtoull** i **wcstoull** używać bieżących ustawień regionalnych; **_strtoull_l** i **_wcstoull_l** zamiast tego użyj ustawień regionalnych, które są przekazywane, ale są identyczne w przeciwnym razie. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

Jeśli *endptr* nie jest **null**, wskaźnik do znaku, który zatrzymał skanowanie jest przechowywany w miejscu, które jest wskazywane przez *endptr*. Jeśli nie można przeprowadzić konwersji (nie znaleziono prawidłowych cyfr lub określono nieprawidłową bazę), wartość *strSource* jest przechowywana w lokalizacji wskazanej przez *endptr*.

**wcstoull** jest szerokoznakową wersją **strtoull,** a jego argument *strSource* jest ciągiem znaków o szerokim charakterze. W przeciwnym razie te funkcje zachowują się identycznie.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoull**|**strtoull**|**strtoull**|**wcstoull**|
|**_tcstoull_l**|**strtoull_l**|**_strtoull_l**|**_wcstoull_l**|

**strtoull** oczekuje *strSource* wskazać ciąg następującej postaci:

> [*odstępy*] [{**+** &#124; **-**}] [**0** [{ **x** &#124; **X** }]] [*cyfry* &#124; *litery*]

*Odstępy* mogą składać się ze znaków spacji i tabulacji, które są ignorowane. *cyfry* są co najmniej jedną cyfrą dziesiętną. *litery* są jedną lub kilkoma literami "a" przez "z" (lub "A" do "Z"). Pierwszy znak, który nie pasuje do tego formularza, zatrzymuje skanowanie. Jeśli *podstawa* znajduje się między 2 a 36, jest używana jako podstawa liczby. Jeśli *baza* wynosi 0, początkowe znaki ciągu, który jest wskazyny przez *strSource* są używane do określenia bazy. Jeśli pierwszy znak to "0", a drugi znak nie jest "x" lub "X", ciąg jest interpretowany jako ósemkowa liczba całkowita. Jeśli pierwszy znak to "0", a drugi znak to "x" lub "X", ciąg jest interpretowany jako liczba całkowita szesnastkowa. Jeśli pierwszy znak jest od 1 do "9", ciąg jest interpretowany jako liczba całkowita dziesiętna. Literom "a" do "z" (lub "A" do "Z") przypisuje się wartości od 10 do 35; tylko litery, których przypisane wartości są mniejsze niż *podstawy* są dozwolone. Pierwszy znak poza zakresem podstawy zatrzymuje skanowanie. Na przykład, jeśli *podstawa* wynosi 0, a pierwszy zeskanowany znak to "0", zakłada się ósemkową ćgiętę całkowitą, a znak "8" lub "9" zatrzymuje skanowanie. **strtoull** umożliwia znak**+** plus ( )**-** lub znak minus ( ) prefiks; wiodący znak minus wskazuje, że zwracana wartość jest negowana.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**strtoull**|\<>|
|**wcstoull**|\<> lub \<wchar.h>|
|**_strtoull_l**|\<>|
|**_wcstoull_l**|\<> lub \<wchar.h>|

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
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[strtoll, _strtoll_l, wcstoll, _wcstoll_l](strtoll-strtoll-l-wcstoll-wcstoll-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
