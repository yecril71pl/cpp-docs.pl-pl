---
title: strtof, _strtof_l, wcstof, _wcstof_l | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _strtof_l
- wcstof
- strtof
- _wcstof_l
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
- _tcstof
- _tcstof_l
- stdlib/strtof
- strtof
- stdlib/_strtof_l
- _strtof_l
- corecrt_wstdlib/wcstof
- wcstof
- corecrt_wstdlib/_wcstof_l
- _wcstof_l
dev_langs:
- C++
helpviewer_keywords:
- _strtof_l function
- _tcstof function
- _wcstof_l function
- wcstof function
- _tcstof_l function
- strtof function
ms.assetid: 52221b46-876d-4fcc-afb1-97512c17a43b
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9e084140b3b220df04859f4ac1bdfe3c1e34ddfc
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="strtof-strtofl-wcstof-wcstofl"></a>strtof, _strtof_l, wcstof, _wcstof_l

Konwertuje wartość zmiennoprzecinkową o pojedynczej dokładności ciągów.

## <a name="syntax"></a>Składnia

```C
float strtof(
   const char *strSource,
   char **endptr
);
float _strtof_l(
   const char *strSource,
   char **endptr,
   _locale_t locale
);
float wcstof(
   const wchar_t *strSource,
   wchar_t **endptr
);
float wcstof_l(
   const wchar_t *strSource,
   wchar_t **endptr,
   _locale_t locale
);
```

## <a name="parameters"></a>Parametry

*strSource*<br/>
Zerem ciąg do konwersji.

*endptr*<br/>
Wskaźnik do znaku, który zatrzymuje skanowania.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

**strtof —** zwraca wartość liczby zmiennoprzecinkowej, z wyjątkiem przypadków, gdy reprezentacja mogłoby spowodować przepełnienie, w którego przypadku funkcja zwraca +/-**HUGE_VALF**. Znak **HUGE_VALF** znak wartość, która nie może być przedstawiony jest zgodna. **strtof —** zwraca wartość 0, jeśli konwersja nie można wykonać lub niedopełnienie występuje.

**wcstof —** zwraca wartości analogously do **strtof —**. Dla obu tych funkcji **errno** ustawiono **erange —** Jeśli występuje przepełnienie lub niedomiar i program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md).

Aby uzyskać więcej informacji na temat kody powrotu, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Funkcja każdego konwertuje ciąg wejściowy *strSource* do **float**. **Strtof —** funkcji konwertuje *strSource* wartości pojedynczej precyzji. **strtof —** przestaje czytać ciąg *strSource* pierwszego znaku nie jest rozpoznawana jako część liczby. Może to być znak końcowy null. **wcstof —** jest wersja znaków dwubajtowych **strtof —**; *strSource* argument jest ciąg znaków dwubajtowych. W przeciwnym razie funkcje te działają tak samo.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstof —**|**strtof**|**strtof**|**wcstof**|
|**_tcstof_l —**|**_strtof_l**|**_strtof_l**|**_wcstof_l**|

**Lc_numeric —** ustawienie kategorii bieżące ustawienia regionalne określa rozpoznawania znaku podstawa w *strSource*; Aby uzyskać więcej informacji, zobacz [setlocale, _wsetlocale —](setlocale-wsetlocale.md). Funkcje, które nie mają **_l** bieżące ustawienia regionalne używać sufiksu; te, które mają sufiks są identyczne, z wyjątkiem tego, aby były używane ustawienia regionalne, który jest przekazywany w zamian. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

Jeśli *endptr* nie jest **NULL**, wskaźnik do znaku zatrzymania skanowania są przechowywane w lokalizacji, która jest wskazywana przez *endptr*. Jeśli konwersja nie można wykonać (nie znaleziono żadnych prawidłowych cyfr lub określono nieprawidłowy atrybut podstawowy), wartość *strSource* są przechowywane w lokalizacji, która jest wskazywana przez *endptr*.

**strtof —** oczekuje *strSource* wskaż ciąg następującą postać:

[*odstępem*] [*znak*] [*cyfr*] [__.__ *cyfr*] [{**e** &#124; **E**} [*znak*] *cyfr*]

A *odstępem* może zawierać znaków miejsca i karty, które są ignorowane. *znak* jest plus (**+**) lub minus (**-**); i *cyfr* są co najmniej jeden cyfr dziesiętnych. Jeśli cyfr nie pojawia się przed znakiem podstawa, co najmniej jeden musi występować po znaku podstawę systemu liczbowego. Wykładnik, obejmującego wprowadzające litery może zawierać wyłącznie cyfr dziesiętnych (**e** lub **E**) i opcjonalnie całkowita. Jeśli pojawi się części wykładnika ani znaków podstawa, znak radix — zakłada się, że wykonaj ostatnich cyfr w ciągu. Pierwszy znak należący do tego formularza zatrzymuje skanowania.

Biblioteka UCRT wersje tych funkcji nie obsługują konwersji Fortran stylu (**d** lub **D**) wykładnika litery. To rozszerzenie niestandardowe była obsługiwana przez wcześniejsze wersje CRT i może być istotne zmiany kodu.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**strtof —**, **_strtof_l —**|C: \<stdlib.h > C++: &lt;cstdlib — > lub \<stdlib.h >|
|**wcstof —**, **_wcstof_l —**|C: \<stdlib.h > lub \<wchar.h > C++: &lt;cstdlib — >, \<stdlib.h > lub \<wchar.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_strtof.c
// This program uses strtof to convert a
// string to a single-precision value.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char *string;
   char *stopstring;
   float x;

   string = "3.14159This stopped it";
   x = strtof(string, &stopstring);
   printf("string = %s\n", string);
   printf("   strtof = %f\n", x);
   printf("   Stopped scan at: %s\n\n", stopstring);
}
```

```Output
string = 3.14159This stopped it
   strtof = 3.141590
   Stopped scan at: This stopped it
```

## <a name="see-also"></a>Zobacz także

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[Konwertowanie ciągów na wartości](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtol, wcstol, _strtol_l, _wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[localeconv](localeconv.md)<br/>
[_create_locale, _wcreate_locale](create-locale-wcreate-locale.md)<br/>
[_free_locale](free-locale.md)<br/>
