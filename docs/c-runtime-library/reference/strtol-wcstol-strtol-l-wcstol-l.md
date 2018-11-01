---
title: strtol, wcstol, _strtol_l, _wcstol_l
ms.date: 11/04/2016
apiname:
- strtol
- wcstol
- _strtol_l
- _wcstol_l
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
ms.openlocfilehash: 5aa69a44a2ce8bde0ee16b02ecd9923f247c7e65
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50617467"
---
# <a name="strtol-wcstol-strtoll-wcstoll"></a>strtol, wcstol, _strtol_l, _wcstol_l

Konwertowanie ciągów na wartość całkowita.

## <a name="syntax"></a>Składnia

```C
long strtol(
   const char *strSource,
   char **endptr,
   int base
);
long wcstol(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base
);
long _strtol_l(
   const char *strSource,
   char **endptr,
   int base,
   _locale_t locale
);
long _wcstol_l(
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

**strtol —** zwraca wartość reprezentowana w ciągu *strSource*, gdy ta reprezentacja spowodowałoby przepełnienie, z wyjątkiem przypadków, jego zwraca **LONG_MAX** lub **LONG_ MIN**. **strtol —** zwraca wartość 0, jeśli nie można wykonać konwersji. **wcstol —** zwraca wartości analogicznie do **strtol —**. Dla obu funkcji **errno** ustawiono **ERANGE** Jeśli występuje przepełnienie lub niedopełnienie.

Zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) Aby uzyskać więcej informacji na temat tych i innych kodów zwrotu.

## <a name="remarks"></a>Uwagi

**Strtol —** funkcji konwertuje *strSource* do **długie**. **strtol —** przestaje odczytywać ciąg *strSource* przy pierwszym znaku, nie może rozpoznać jako elementu liczby. Może to być kończący znak null lub pierwszy znak numeryczny, większa niż lub równa może być *podstawowy*.

**wcstol —** to wersja znaku dwubajtowego **strtol —**; jej *strSource* argumentu jest ciągiem znaku dwubajtowego. Funkcje te zachowują się identycznie.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstol —**|**strtol**|**strtol**|**wcstol**|
|**_tcstol_l**|**_strtol_l**|**_strtol_l**|**_wcstol_l**|

Bieżące ustawienia regionalne **LC_NUMERIC** ustawienie kategorii określa rozpoznawanie znaku podstawy w parametrze *strSource **;* Aby uzyskać więcej informacji, zobacz [setlocale](setlocale-wsetlocale.md). Funkcje bez **_l** sufiksa używa bieżących ustawień regionalnych; **_strtol_l —** i **_wcstol_l —** są identyczne z odpowiednimi funkcjami bez **_l** sufiks z tą różnicą, że używają w zamian przekazanych ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

Jeśli *endptr* nie **NULL**, wskaźnik znaku, który zatrzymał skanowanie jest przechowywany w lokalizacji wskazywanej przez *endptr*. Jeśli konwersja nie może być wykonywana (nie znaleziono żadnych prawidłowych cyfr lub określono nieprawidłową podstawę), wartość *strSource* jest przechowywany w lokalizacji wskazywanej przez *endptr*.

**strtol —** oczekuje *strSource* do wskaże ciąg o następującej postaci:

> [*odstępu*] [{**+** &#124; **-**}] [**0** [{ **x** &#124; **X** }]] [*cyfr* &#124; *litery*]  

A *odstępu* może składać się ze znaków spacji lub tabulatora, które są ignorowane. *cyfr* są co najmniej jedna cyfra dziesiętna; *litery* są co najmniej liter "" do "z" (lub "A" do "Z").  Pierwszy znak, który nie mieści się tym formularzu zatrzymuje skanowanie. Jeśli *podstawowy* jest między 2 a 36, zostanie użyty jako podstawa numeru. Jeśli *podstawowy* ma wartość 0, początkowe znaki ciągu wskazywany przez *strSource* są używane do określenia podstawy. Jeśli pierwszym znakiem jest 0, a drugim znakiem nie jest,, x"lub,, X", ciąg jest interpretowany jako ósemkowa liczba całkowita. Jeśli pierwszym znakiem jest "0", a drugim znakiem jest,, x"lub,, X", ciąg jest interpretowany jako szesnastkowa liczba całkowita. Jeśli pierwszym znakiem jest,, 1 "do,, 9", ciąg jest interpretowany jako dziesiętna liczba całkowita. Litery od "" do "z" (lub "" – "Z") są przypisane wartości od 10 do 35; tylko litery, w których przypisane wartości są mniej niż *podstawowy* są dozwolone. Pierwszy znak spoza zakresu podstawy zatrzymuje skanowanie. Na przykład jeśli *podstawowy* wynosi 0 i pierwszy znak skanowany to "0", zakłada, że ósemkowa liczba całkowitej i znaku "8" lub "9" zatrzyma skanowanie.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**strtol**|\<stdlib.h>|
|**wcstol**|\<stdlib.h > lub \<wchar.h >|
|**_strtol_l**|\<stdlib.h>|

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
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
