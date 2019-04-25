---
title: strtoimax, _strtoimax_l, wcstoimax, _wcstoimax_l
ms.date: 11/04/2016
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
helpviewer_keywords:
- strtoimax funciton
- conversion functions
- _strtoimax_l function
- _wcstoimax_l function
- wcstoimax function
ms.assetid: 4530d3dc-aaac-4a76-b7cf-29ae3c98d0ae
ms.openlocfilehash: e0a320f90b2c0f8653109a6ae0056c4c0cdd7455
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62176294"
---
# <a name="strtoimax-strtoimaxl-wcstoimax-wcstoimaxl"></a>strtoimax, _strtoimax_l, wcstoimax, _wcstoimax_l

Konwertuje ciąg na wartość całkowitą typu największa oznaczona obsługiwana liczba całkowita.

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
Ciąg zakończony wartością null do konwersji.

*endptr*<br/>
Wskaźnik znaku zatrzymującego skanowanie.

*base*<br/>
Numer podstawowy do użycia.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

**strtoimax** zwraca wartość, która jest reprezentowana w ciągu *strSource*, z wyjątkiem sytuacji, gdy ta reprezentacja spowodowałoby przepełnienie — w takiej sytuacji zwraca **INTMAX_MAX** lub **INTMAX_MIN**, i **errno** ustawiono **ERANGE**. Funkcja zwraca 0, jeśli nie można wykonać konwersji. **wcstoimax —** zwraca wartości analogicznie do **strtoimax**.

**INTMAX_MAX** i **INTMAX_MIN** są zdefiniowane w stdint.h.

Jeśli *strSource* jest **NULL** lub *podstawowy* jest różna od zera i albo mniejszy niż 2 albo większy niż 36, atrybut **errno** ustawiono **EINVAL** .

Aby uzyskać więcej informacji na temat kodów powrotnych, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**Strtoimax** funkcji konwertuje *strSource* do **intmax_t**. Wersja znaków dwubajtowych **strtoimax** jest **wcstoimax —**; jej *strSource* argumentu jest ciągiem znaku dwubajtowego. W przeciwnym wypadku te funkcje zachowują się identycznie. Obie funkcje przestają odczytywać ciąg *strSource* przy pierwszym znaku, ich nie może rozpoznać jako elementu liczby. Może to być kończący znak null lub pierwszy znak numeryczny, który jest większy niż lub równa może być *podstawowy*.

Ustawienia regionalne **LC_NUMERIC** ustawienie kategorii określa rozpoznawanie znaku podstawy w parametrze *strSource*; Aby uzyskać więcej informacji, zobacz [setlocale, _wsetlocale](setlocale-wsetlocale.md). Funkcje, które nie mają **_l** sufiksa używa bieżących ustawień regionalnych; **_strtoimax_l —** i **_wcstoimax_l —** są identyczne z odpowiednimi funkcjami, które nie mają **_l** sufiks z tą różnicą, że używają w zamian ustawień regionalnych to przekazana. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

Jeśli *endptr* nie **NULL**, wskaźnik znaku, który zatrzymał skanowanie jest przechowywany w lokalizacji, która jest wskazywany przez *endptr*. Jeśli konwersja nie może być wykonywana (nie znaleziono żadnych prawidłowych cyfr lub określono nieprawidłową podstawę), wartość *strSource* znajduje się w lokalizacji, która jest wskazywany przez *endptr*.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoimax**|**strtoimax**|**strtoimax**|**wcstoimax**|
|**_tcstoimax_l**|**strtoimax_l**|**_strtoimax_l**|**_wcstoimax_l**|

**strtoimax** oczekuje *strSource* do wskaże ciąg o następującej postaci:

> [*odstępu*] [{**+** &#124; **-**}] [**0** [{ **x** &#124; **X** }]] [*cyfr* &#124; *litery*]  

A *odstępu* może składać się ze znaków spacji lub tabulatora, które są ignorowane. *cyfr* są co najmniej jedna cyfra dziesiętna; *litery* są co najmniej liter "" do "z" (lub "A" do "Z"). Pierwszy znak, który nie mieści się tym formularzu zatrzymuje skanowanie. Jeśli *podstawowy* jest między 2 a 36, zostanie użyty jako podstawa numeru. Jeśli *podstawowy* ma wartość 0, początkowe znaki ciągu wskazywany przez *strSource* są używane do określenia podstawy. Jeśli pierwszym znakiem jest "0", a drugim znakiem nie jest,, x"lub,, X", ciąg jest interpretowany jako ósemkowa liczba całkowita. Jeśli pierwszym znakiem jest "0", a drugim znakiem jest,, x"lub,, X", ciąg jest interpretowany jako szesnastkowa liczba całkowita. Jeśli pierwszym znakiem jest,, 1 "do,, 9", ciąg jest interpretowany jako dziesiętna liczba całkowita. Litery od "" do "z" (lub "" – "Z") są przypisane wartości od 10 do 35; tylko litery, w których przypisane wartości są mniej niż *podstawowy* są dozwolone. Pierwszy znak spoza zakresu podstawy zatrzymuje skanowanie. Na przykład jeśli *podstawowy* wynosi 0 i pierwszy znak skanowany to "0", zakłada, że ósemkowa liczba całkowitej i "8" lub "9" zatrzymałoby skanowania.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**strtoimax**, **_strtoimax_l**, **wcstoimax**, **_wcstoimax_l**|\<inttypes.h>|

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
