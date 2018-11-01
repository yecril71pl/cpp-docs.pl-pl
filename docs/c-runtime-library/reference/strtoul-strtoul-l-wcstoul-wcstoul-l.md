---
title: strtoul, _strtoul_l, wcstoul, _wcstoul_l
ms.date: 11/04/2016
apiname:
- _wcstoul_l
- _strtoul_l
- strtoul
- wcstoul
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
ms.openlocfilehash: c1ef17b7b5cf1dac2d10cd16889241c40f89a507
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50436151"
---
# <a name="strtoul-strtoull-wcstoul-wcstoull"></a>strtoul, _strtoul_l, wcstoul, _wcstoul_l

Konwertowanie ciągów na wartość całkowita bez znaku.

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

*strSource*<br/>
Ciąg zakończony wartością null do konwersji.

*endptr*<br/>
Wskaźnik znaku zatrzymującego skanowanie.

*base*<br/>
Numer podstawowy do użycia.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

**strtoul —** zwraca przekonwertowana wartości, jeśli istnieje, lub **ULONG_MAX** przy przepełnieniu. **strtoul —** zwraca wartość 0, jeśli nie można wykonać konwersji. **wcstoul —** zwraca wartości analogicznie do **strtoul —**. Dla obu funkcji **errno** ustawiono **ERANGE** Jeśli występuje przepełnienie lub niedopełnienie.

Zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) kody powrotne — Aby uzyskać więcej informacji na temat tego i innych.

## <a name="remarks"></a>Uwagi

Każda z tych funkcji konwertuje ciąg wejściowy *strSource* do **niepodpisane** **długie**.

**strtoul —** przestaje odczytywać ciąg *strSource* przy pierwszym znaku, nie może rozpoznać jako elementu liczby. Może to być kończący znak null lub pierwszy znak numeryczny, większa niż lub równa może być *podstawowy*. **LC_NUMERIC** ustawienia kategorii ustawień regionalnych określa rozpoznawanie znaku podstawy w parametrze *strSource*; Aby uzyskać więcej informacji, zobacz [setlocale](setlocale-wsetlocale.md). **strtoul —** i **wcstoul —** Użyj bieżących ustawień regionalnych; **_strtoul_l —** i **_wcstoul_l —** są identyczne, z tą różnicą, że używają w zamian przekazanych ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

Jeśli *endptr* nie **NULL**, wskaźnik znaku, który zatrzymał skanowanie jest przechowywany w lokalizacji wskazywanej przez *endptr*. Jeśli konwersja nie może być wykonywana (nie znaleziono żadnych prawidłowych cyfr lub określono nieprawidłową podstawę), wartość *strSource* jest przechowywany w lokalizacji wskazywanej przez *endptr*.

**wcstoul —** to wersja znaku dwubajtowego **strtoul —**; jej *strSource* argumentu jest ciągiem znaku dwubajtowego. W przeciwnym razie te funkcje zachowują się identycznie.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoul —**|**strtoul**|**strtoul**|**wcstoul**|
|**_tcstoul_l**|**strtoul_l —**|**_strtoul_l**|**_wcstoul_l**|

**strtoul —** oczekuje *strSource* do wskaże ciąg o następującej postaci:

> [*odstępu*] [{**+** &#124; **-**}] [**0** [{ **x** &#124; **X** }]] [*cyfr* &#124; *litery*]  

A *odstępu* może składać się ze znaków spacji lub tabulatora, które są ignorowane. *cyfry* są co najmniej jedna cyfra dziesiętna. *litery* są co najmniej liter "" do "z" (lub "A" do "Z"). Pierwszy znak, który nie mieści się tym formularzu zatrzymuje skanowanie. Jeśli *podstawowy* jest między 2 a 36, zostanie użyty jako podstawa numeru. Jeśli *podstawowy* ma wartość 0, początkowe znaki ciągu wskazywany przez *strSource* są używane do określenia podstawy. Jeśli pierwszym znakiem jest 0, a drugim znakiem nie jest,, x"lub,, X", ciąg jest interpretowany jako ósemkowa liczba całkowita. Jeśli pierwszym znakiem jest "0", a drugim znakiem jest,, x"lub,, X", ciąg jest interpretowany jako szesnastkowa liczba całkowita. Jeśli pierwszym znakiem jest,, 1 "do,, 9", ciąg jest interpretowany jako dziesiętna liczba całkowita. Litery od "" do "z" (lub "" – "Z") są przypisane wartości od 10 do 35; tylko litery, w których przypisane wartości są mniej niż *podstawowy* są dozwolone. Pierwszy znak spoza zakresu podstawy zatrzymuje skanowanie. Na przykład jeśli *podstawowy* wynosi 0 i pierwszy znak skanowany to "0", zakłada, że ósemkowa liczba całkowitej i znaku "8" lub "9" zatrzyma skanowanie. **strtoul —** umożliwia znakiem plus (**+**) lub minus (**-**) prefiksu logowania; wiodący znak minus wskazuje, że wartość zwracana jest ujemna.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**strtoul**|\<stdlib.h>|
|**wcstoul**|\<stdlib.h > lub \<wchar.h >|
|**_strtoul_l**|\<stdlib.h>|
|**_wcstoul_l**|\<stdlib.h > lub \<wchar.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [strtod](strtod-strtod-l-wcstod-wcstod-l.md).

## <a name="see-also"></a>Zobacz także

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[Konwertowanie ciągów na wartości](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtol, wcstol, _strtol_l, _wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
