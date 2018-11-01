---
title: strtoumax, _strtoumax_l, wcstoumax, _wcstoumax_l
ms.date: 11/04/2016
apiname:
- _wcstoumax_l
- _strtoumax_l
- wcstoumax
- strtoumax
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
- wcstoumax
- _tcstoumax
- _strtoumax_l
- _wcstoumax_l
- _tcstoumax_l
- strtoumax
helpviewer_keywords:
- _strtoumax_l function
- conversion functions
- wcstoumax function
- _wcstoumax_l function
- strtoumax function
ms.assetid: 566769f9-495b-4508-b9c6-02217a578897
ms.openlocfilehash: c9c8ca79ed68b23586d9fef979bc8d47b72ca846
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50518472"
---
# <a name="strtoumax-strtoumaxl-wcstoumax-wcstoumaxl"></a>strtoumax, _strtoumax_l, wcstoumax, _wcstoumax_l

Konwertuje ciągi na wartość całkowitą typu największa obsługiwana liczba całkowita bez znaku.

## <a name="syntax"></a>Składnia

```C
uintmax_t strtoumax(
   const char *strSource,
   char **endptr,
   int base
);
uintmax_t _strtoumax_l(
   const char *strSource,
   char **endptr,
   int base,
   _locale_t locale
);
uintmax_t wcstoumax(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base
);
uintmax_t _wcstoumax_l(
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

**strtoumax —** zwraca przekonwertowana wartości, jeśli istnieje, lub **UINTMAX_MAX** przy przepełnieniu. **strtoumax —** zwraca wartość 0, jeśli nie można wykonać konwersji. **wcstoumax —** zwraca wartości analogicznie do **strtoumax —**. Dla obu funkcji **errno** ustawiono **ERANGE** Jeśli występuje przepełnienie lub niedopełnienie.

Aby uzyskać więcej informacji na temat kodów powrotnych, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Każda z tych funkcji konwertuje ciąg wejściowy *strSource* do **uintmax_t** wartość całkowitą.

**strtoumax —** przestaje odczytywać ciąg *strSource* przy pierwszym znaku, nie może rozpoznać jako elementu liczby. Może to być kończący znak null lub pierwszy znak numeryczny, który jest większy niż lub równa może być *podstawowy*. **LC_NUMERIC** ustawienia kategorii ustawień regionalnych określa rozpoznawanie znaku podstawy w parametrze *strSource*. Aby uzyskać więcej informacji, zobacz [setlocale, _wsetlocale](setlocale-wsetlocale.md). **strtoumax —** i **wcstoumax —** Użyj bieżących ustawień regionalnych; **_strtoumax_l —** i **_wcstoumax_l —** są identyczne, z tą różnicą, że używają w zamian ustawień regionalnych, które zostały przekazane. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

Jeśli *endptr* nie **NULL**, wskaźnik znaku, który zatrzymał skanowanie jest przechowywany w lokalizacji, która jest wskazywany przez *endptr*. Jeśli konwersja nie może być wykonywana (nie znaleziono żadnych prawidłowych cyfr lub określono nieprawidłową podstawę), wartość *strSource* znajduje się w lokalizacji, która jest wskazywany przez *endptr*.

Wersja znaków dwubajtowych **strtoumax —** jest **wcstoumax —**; jej *strSource* argumentu jest ciągiem znaku dwubajtowego. W przeciwnym wypadku te funkcje zachowują się identycznie.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoumax**|**strtoumax**|**strtoumax**|**wcstoumax**|
|**_tcstoumax_l**|**strtoumax_l**|**_strtoumax_l —**|**_wcstoumax_l**|

**strtoumax —** oczekuje *strSource* do wskaże ciąg o następującej postaci:

> [*odstępu*] [{**+** &#124; **-**}] [**0** [{ **x** &#124; **X** }]] [*cyfr* &#124; *litery*]  

A *odstępu* może składać się ze znaków spacji lub tabulatora, które są ignorowane. *cyfry* są co najmniej jedna cyfra dziesiętna. *litery* są co najmniej liter "" do "z" (lub "A" do "Z"). Pierwszy znak, który nie mieści się tym formularzu zatrzymuje skanowanie. Jeśli *podstawowy* jest między 2 a 36, zostanie użyty jako podstawa numeru. Jeśli *podstawowy* ma wartość 0, początkowe znaki ciągu, który jest wskazywany przez *strSource* są używane do określenia podstawy. Jeśli pierwszym znakiem jest "0", a drugim znakiem nie jest,, x"lub,, X", ciąg jest interpretowany jako ósemkowa liczba całkowita. Jeśli pierwszym znakiem jest "0", a drugim znakiem jest,, x"lub,, X", ciąg jest interpretowany jako szesnastkowa liczba całkowita. Jeśli pierwszym znakiem jest,, 1 "do,, 9", ciąg jest interpretowany jako dziesiętna liczba całkowita. Litery od "" do "z" (lub "" – "Z") są przypisane wartości od 10 do 35; tylko litery, w których przypisane wartości są mniej niż *podstawowy* są dozwolone. Pierwszy znak spoza zakresu podstawy zatrzymuje skanowanie. Na przykład jeśli *podstawowy* wynosi 0 i pierwszy znak skanowany to "0", zakłada, że ósemkowa liczba całkowitej i "8" lub "9" zatrzymałoby skanowania. **strtoumax —** zezwala na znak plus (**+**) lub znak minus (**-**) prefiks; wiodący znak minus wskazuje, że wartość zwracana jest uzupełnieniem do dwóch wartości bezwzględnej przekonwertowanego ciągu.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**strtoumax**|\<stdlib.h>|
|**wcstoumax**|\<stdlib.h > lub \<wchar.h >|
|**_strtoumax_l —**|\<stdlib.h>|
|**_wcstoumax_l**|\<stdlib.h > lub \<wchar.h >|

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
[strtoimax, _strtoimax_l, wcstoimax, _wcstoimax_l](strtoimax-strtoimax-l-wcstoimax-wcstoimax-l.md)<br/>
[strtol, wcstol, _strtol_l, _wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[strtoll, _strtoll_l, wcstoll, _wcstoll_l](strtoll-strtoll-l-wcstoll-wcstoll-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
