---
title: _strtoui64, _wcstoui64, _strtoui64_l, _wcstoui64_l
ms.date: 11/04/2016
api_name:
- _strtoui64
- _strtoui64_l
- _wcstoui64
- _wcstoui64_l
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
ms.openlocfilehash: be7d779bac50d332dde879c9d5b070fd2bf7e7e5
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70946429"
---
# <a name="_strtoui64-_wcstoui64-_strtoui64_l-_wcstoui64_l"></a>_strtoui64, _wcstoui64, _strtoui64_l, _wcstoui64_l

Konwertuj ciąg na wartość unsigned **__int64** .

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

*strSource*<br/>
Ciąg zakończony znakiem null do przekonwertowania.

*endptr*<br/>
Wskaźnik do znaku, który powoduje zatrzymanie skanowania.

*base*<br/>
Numer bazowy do użycia.

*ustawienie*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

**_strtoui64** zwraca wartość reprezentowaną w ciągu *strSource*, z wyjątkiem sytuacji, gdy reprezentacja spowodowałoby przepełnienie, w takim przypadku zwraca **_UI64_MAX**. **_strtoui64** zwraca wartość 0, jeśli nie można wykonać konwersji.

**_UI64_MAX** jest zdefiniowany w limitach. C.

Jeśli *strSource* ma **wartość null** lub *podstawa* jest różna od zera i jest mniejsza niż 2 lub większa niż 36, **errno** jest ustawiona na **EINVAL**.

Zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) , aby uzyskać więcej informacji na temat tych i innych kodów powrotu.

## <a name="remarks"></a>Uwagi

Funkcja **_strtoui64** konwertuje *strSource* na **niepodpisane** **__int64**. **_wcstoui64** to dwubajtowa wersja **_strtoui64**; jego argument *strSource* jest ciągiem znaków dwubajtowych. W przeciwnym razie te funkcje zachowują się identycznie.

Obie funkcje przerywają odczytywanie ciągu *strSource* na pierwszym znaku, którego nie mogą rozpoznać jako części liczby. Może to być kończący znak null lub może być pierwszym znakiem numerycznym większym lub równym *Base*.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _UNICODE & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoui64**|**_strtoui64**|**_strtoui64**|**_wstrtoui64**|
|**_tcstoui64_l**|**_strtoui64_l**|**_strtoui64_l**|**_wstrtoui64_l**|

Ustawienie kategorii **LC_NUMERIC** bieżących ustawień regionalnych określa rozpoznawanie znaku podstawy w *strSource*; Aby uzyskać więcej informacji, zobacz [setlocale](setlocale-wsetlocale.md). Funkcje bez sufiksu _l używają bieżących ustawień regionalnych; **_strtoui64_l** i **_wcstoui64_l** są identyczne z odpowiednimi funkcjami bez sufiksu **_l** , z tą różnicą, że w zamian korzystają z przekazaną ustawieniami regionalnymi. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

Jeśli *endptr* nie ma **wartości null**, wskaźnik do znaku, który zatrzymał skanowanie jest przechowywany w lokalizacji wskazywanej przez *endptr*. Jeśli konwersja nie może być wykonywana (nie znaleziono prawidłowych cyfr lub określono nieprawidłową podstawę), wartość *strSource* jest przechowywana w lokalizacji wskazywanej przez *endptr*.

**_strtoui64** oczekuje, że *strSource* wskazuje ciąg o następującej postaci:

> [*odstęp*] [{ **+** &#124; &#124; &#124; }] [0 [{x x}]] [cyfry cyfr] **-**

*Odstępy* mogą zawierać spacje i znaki tabulacji, które są ignorowane. *cyfry* to co najmniej jedna cyfra dziesiętna. *litery* są jedną lub większą literą od "a" do "z" (lub od "a" do "z"). Pierwszy znak, który nie pasuje do tego formularza, zatrzyma skanowanie. Jeśli *baza* jest z przedziału od 2 do 36, zostanie użyta jako podstawa liczby. Jeśli *Base* ma wartość 0, początkowe znaki ciągu wskazywane przez *strSource* są używane do określenia podstawy. Jeśli pierwszym znakiem jest 0, a drugi znak nie jest "x" lub "X", ciąg jest interpretowany jako ósemkowa liczba całkowita. Jeśli pierwszy znak to "0", a drugi znak to "x" lub "X", ciąg jest interpretowany jako Szesnastkowa liczba całkowita. Jeśli pierwszym znakiem jest "1" do "9", ciąg jest interpretowany jako dziesiętna liczba całkowita. Litery od "a" do "z" (lub "A" do "z") mają przypisane wartości od 10 do 35; dozwolone są tylko litery, których przypisane wartości są mniejsze niż *podstawowe* . Pierwszy znak poza zakresem podstawy powoduje zatrzymanie skanowania. Na przykład jeśli *Base* ma wartość 0, a pierwszy znak skanowany to "0", zakłada się liczbę całkowitą, a znak "8" lub "9" spowoduje zatrzymanie skanowania.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_strtoui64**|\<stdlib.h>|
|**_wcstoui64**|\<STDLIB. h > lub \<WCHAR. h >|
|**_strtoui64_l**|\<stdlib.h>|
|**_wcstoui64_l**|\<STDLIB. h > lub \<WCHAR. h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz także

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[Konwertowanie ciągów na wartości](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
