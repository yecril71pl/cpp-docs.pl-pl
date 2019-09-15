---
title: strtoumax, _strtoumax_l, wcstoumax, _wcstoumax_l
ms.date: 11/04/2016
api_name:
- _wcstoumax_l
- _strtoumax_l
- wcstoumax
- strtoumax
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
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: a4ed09ad51e538f3964fea87fa55e410c79d3a5d
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957688"
---
# <a name="strtoumax-_strtoumax_l-wcstoumax-_wcstoumax_l"></a>strtoumax, _strtoumax_l, wcstoumax, _wcstoumax_l

Konwertuje ciągi na wartość całkowitą największego obsługiwanego typu Liczba całkowita bez znaku.

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
Ciąg zakończony znakiem null do przekonwertowania.

*endptr*<br/>
Wskaźnik do znaku, który zatrzyma skanowanie.

*base*<br/>
Numer bazowy do użycia.

*ustawienie*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

**strtoumax** zwraca przekonwertowaną wartość, jeśli istnieje, lub **UINTMAX_MAX** w przypadku przepełnienia. **strtoumax** zwraca wartość 0, jeśli nie można wykonać konwersji. **wcstoumax** zwraca wartości analogicznie do **strtoumax**. Dla obu funkcji **errno** jest ustawiony na **ERANGE** , jeśli występuje przepełnienie lub nadmiar.

Aby uzyskać więcej informacji na temat kodów powrotnych, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Każda z tych funkcji konwertuje ciąg wejściowy *strSource* na wartość **uintmax_t** Integer.

**strtoumax** przestaje odczytywania ciągu *strSource* przy pierwszym znaku, którego nie może rozpoznać jako części liczby. Może to być kończący znak null lub może być pierwszym znakiem numerycznym, który jest większy lub równy *Base*. Ustawienie kategorii **LC_NUMERIC** ustawień regionalnych określa rozpoznawanie znaku podstawy w *strSource*. Aby uzyskać więcej informacji, zobacz [setlocals, _wsetlocale](setlocale-wsetlocale.md). **strtoumax** i **wcstoumax** używają bieżących ustawień regionalnych; **_strtoumax_l** i **_wcstoumax_l** są identyczne, z tą różnicą, że zamiast nich używają ustawień regionalnych, które są przesyłane. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

Jeśli *endptr* nie ma **wartości null**, wskaźnik do znaku, który zatrzymał skanowanie jest przechowywany w lokalizacji wskazywanej przez *endptr*. Jeśli konwersja nie może być wykonywana (nie znaleziono prawidłowych cyfr lub określono nieprawidłową podstawę), wartość *strSource* jest przechowywana w lokalizacji wskazywanej przez *endptr*.

Dwubajtowa wersja **strtoumax** jest **wcstoumax**; jego argument *strSource* jest ciągiem znaków dwubajtowych. W przeciwnym razie funkcje te zachowują się identycznie.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _UNICODE & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoumax**|**strtoumax**|**strtoumax**|**wcstoumax**|
|**_tcstoumax_l**|**strtoumax_l**|**_strtoumax_l**|**_wcstoumax_l**|

**strtoumax** oczekuje, że *strSource* wskazuje ciąg o następującej postaci:

> [*odstęp*] [{ **+** &#124; &#124; &#124; }] [0 [{x x}]] [cyfry cyfr] **-**

*Odstępy* mogą zawierać spacje i znaki tabulacji, które są ignorowane. *cyfry* to co najmniej jedna cyfra dziesiętna. *litery* są jedną lub większą literą od "a" do "z" (lub od "a" do "z"). Pierwszy znak, który nie pasuje do tego formularza, zatrzyma skanowanie. Jeśli *baza* jest z przedziału od 2 do 36, zostanie użyta jako podstawa liczby. Jeśli *Base* ma wartość 0, początkowe znaki ciągu, który jest wskazywany przez *strSource* , są używane do określenia podstawy. Jeśli pierwszym znakiem jest "0", a drugi znak nie jest "x" lub "X", ciąg jest interpretowany jako ósemkowa liczba całkowita. Jeśli pierwszy znak to "0", a drugi znak to "x" lub "X", ciąg jest interpretowany jako Szesnastkowa liczba całkowita. Jeśli pierwszym znakiem jest "1" do "9", ciąg jest interpretowany jako dziesiętna liczba całkowita. Litery od "a" do "z" (lub "A" do "z") mają przypisane wartości od 10 do 35; dozwolone są tylko litery, których przypisane wartości są mniejsze niż *podstawowe* . Pierwszy znak poza zakresem podstawy powoduje zatrzymanie skanowania. Na przykład jeśli *Base* ma wartość 0, a pierwszy znak skanowany to "0", zakłada się liczbę całkowitą, a znak "8" lub "9" spowoduje zatrzymanie skanowania. **strtoumax** zezwala na prefiks znaku plus **+** () lub znaku minus **-** (); wiodący znak minus wskazuje, że wartość zwracana jest uzupełnieniem dwóch wartości bezwzględnej przekonwertowanego ciągu.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**strtoumax**|\<stdlib.h>|
|**wcstoumax**|\<STDLIB. h > lub \<WCHAR. h >|
|**_strtoumax_l**|\<stdlib.h>|
|**_wcstoumax_l**|\<STDLIB. h > lub \<WCHAR. h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład dla [strtod](strtod-strtod-l-wcstod-wcstod-l.md).

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
