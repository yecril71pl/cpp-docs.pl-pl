---
title: _strtoui64, _wcstoui64, _strtoui64_l, _wcstoui64_l
ms.date: 4/2/2020
api_name:
- _strtoui64
- _strtoui64_l
- _wcstoui64
- _wcstoui64_l
- _o__strtoui64
- _o__strtoui64_l
- _o__wcstoui64
- _o__wcstoui64_l
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
- _wcstoui64_l
- strtoui64_l
- wcstoui64
- _wcstoui64
- _strtoui64_l
- strtoui64
- _strtoui64
- wcstoui64_l
helpviewer_keywords:
- _strtoui64_l function
- _wcstoui64_l function
- string conversion, to integers
- wcstoui64_l function
- _strtoui64 function
- _wcstoui64 function
- wcstoui64 function
- strtoui64_l function
- strtoui64 function
ms.assetid: 7fcb537e-4554-4ceb-a5b6-bc09244e72ef
ms.openlocfilehash: f3c5631a34c35ed5f5b74e15dfc4225224215b89
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365465"
---
# <a name="_strtoui64-_wcstoui64-_strtoui64_l-_wcstoui64_l"></a>_strtoui64, _wcstoui64, _strtoui64_l, _wcstoui64_l

Konwertuj ciąg na niepodpisaną wartość **__int64.**

## <a name="syntax"></a>Składnia

```C
unsigned __int64 _strtoui64(
   const char *strSource,
   char **endptr,
   int base
);
unsigned __int64 _wcstoui64(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base
);
unsigned __int64 _strtoui64_l(
   const char *strSource,
   char **endptr,
   int base,
   _locale_t locale
);
unsigned __int64 _wcstoui64(
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

**_strtoui64** zwraca wartość reprezentowaną w *strSource*ciągu , z wyjątkiem sytuacji, gdy reprezentacja spowoduje przepełnienie, w którym to przypadku zwraca **_UI64_MAX**. **_strtoui64** zwraca wartość 0, jeśli nie można przeprowadzić konwersji.

**_UI64_MAX** jest zdefiniowany w limitach. H.

Jeśli *strSource* ma **wartość NULL** lub *podstawa* jest niezerowa i mniejsza niż 2 lub większa niż 36, **errno** jest ustawiona na **wartość EINVAL**.

Zobacz [_doserrno, errno, _sys_errlist i _sys_nerr,](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) aby uzyskać więcej informacji na temat tych i innych kodów zwrotnych.

## <a name="remarks"></a>Uwagi

Funkcja **_strtoui64** konwertuje *strSource* na **niepodpisaną** **__int64**. **_wcstoui64** jest szerokoznakową wersją **_strtoui64**; jego *argument strSource* jest ciągiem znaków o szerokim charakterze. W przeciwnym razie te funkcje zachowują się identycznie.

Obie funkcje przestają odczytywać ciąg *strSource* przy pierwszym znaku, który nie może rozpoznać jako część liczby. Może to być kończący się znak null lub pierwszy znak numeryczny większy lub równy *podstawie.*

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoui64**|**_strtoui64**|**_strtoui64**|**_wstrtoui64**|
|**_tcstoui64_l**|**_strtoui64_l**|**_strtoui64_l**|**_wstrtoui64_l**|

Ustawienie **kategorii LC_NUMERIC** bieżącej ustawień ustawień regionalnych określa rozpoznawanie znaku radix w *strSource*; aby uzyskać więcej informacji, zobacz [setlocale](setlocale-wsetlocale.md). Funkcje bez sufiksu _l używają bieżących ustawień regionalnych; **_strtoui64_l** i **_wcstoui64_l** są identyczne z odpowiednimi funkcjami bez sufiksu **_l,** z tą różnicą, że zamiast tego używają ustawień regionalnych przekazanych. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

Jeśli *endptr* nie ma **wartości NULL,** wskaźnik do znaku, który zatrzymał skanowanie jest przechowywany w miejscu wskazanym przez *endptr*. Jeśli nie można przeprowadzić konwersji (nie znaleziono prawidłowych cyfr lub określono nieprawidłową bazę), wartość *strSource* jest przechowywana w lokalizacji wskazanej przez *endptr*.

**_strtoui64** oczekuje *strSource* wskazać ciąg następującego formularza:

> [*odstępy*] [{**+** &#124; **-**}] [**0** [{ **x** &#124; **X** }]] [*cyfry* &#124; *litery*]

*Odstępy* mogą składać się ze znaków spacji i tabulacji, które są ignorowane. *cyfry* są co najmniej jedną cyfrą dziesiętną. *litery* są jedną lub kilkoma literami "a" przez "z" (lub "A" do "Z"). Pierwszy znak, który nie pasuje do tego formularza, zatrzymuje skanowanie. Jeśli *podstawa* znajduje się między 2 a 36, jest używana jako podstawa liczby. Jeśli *podstawa* wynosi 0, początkowe znaki ciągu wskazywowane przez *strSource* są używane do określenia podstawy. Jeśli pierwszy znak ma 0, a drugi znak nie jest "x" lub "X", ciąg jest interpretowany jako ósemkowa liczba całkowita. Jeśli pierwszy znak to "0", a drugi znak to "x" lub "X", ciąg jest interpretowany jako liczba całkowita szesnastkowa. Jeśli pierwszy znak jest od 1 do "9", ciąg jest interpretowany jako liczba całkowita dziesiętna. Literom "a" do "z" (lub "A" do "Z") przypisuje się wartości od 10 do 35; tylko litery, których przypisane wartości są mniejsze niż *podstawy* są dozwolone. Pierwszy znak poza zakresem podstawy zatrzymuje skanowanie. Na przykład, jeśli *podstawa* wynosi 0, a pierwszy zeskanowany znak to "0", zakłada się ósemkową liczę całkowitą, a znak "8" lub "9" zatrzyma skanowanie.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_strtoui64**|\<>|
|**_wcstoui64**|\<> lub \<wchar.h>|
|**_strtoui64_l**|\<>|
|**_wcstoui64_l**|\<> lub \<wchar.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_strtoui64.c
#include <stdio.h>

unsigned __int64 atoui64(const char *szUnsignedInt) {
   return _strtoui64(szUnsignedInt, NULL, 10);
}

int main() {
   unsigned __int64 u = atoui64("18446744073709551615");
   printf( "u = %I64u\n", u );
}
```

```Output
u = 18446744073709551615
```

## <a name="see-also"></a>Zobacz też

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Ustawienia regionalne](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[Ciąg do funkcji wartości liczbowej](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
