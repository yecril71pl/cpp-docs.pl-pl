---
title: strtof, _strtof_l, wcstof, _wcstof_l
ms.date: 04/05/2018
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
helpviewer_keywords:
- _strtof_l function
- _tcstof function
- _wcstof_l function
- wcstof function
- _tcstof_l function
- strtof function
ms.assetid: 52221b46-876d-4fcc-afb1-97512c17a43b
ms.openlocfilehash: 10a50a175685f3e8f7f1241683c7705fd9a9b142
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62376435"
---
# <a name="strtof-strtofl-wcstof-wcstofl"></a>strtof, _strtof_l, wcstof, _wcstof_l

Konwertuje ciągi na wartość zmiennoprzecinkową pojedynczej precyzji.

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
Ciąg zakończony wartością null do konwersji.

*endptr*<br/>
Wskaźnik znaku zatrzymującego skanowanie.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

**strtof —** zwraca wartość zmiennoprzecinkową, z wyjątkiem sytuacji, gdy ta reprezentacja spowodowałoby przepełnienie, w których przypadku funkcja zwraca wartość +/-**HUGE_VALF**. Znak **HUGE_VALF** odpowiada znakowi wartości, który nie może być reprezentowana. **strtof —** zwraca wartość 0, jeśli nie można wykonać konwersji lub występuje niedopełnienie.

**wcstof —** zwraca wartości analogicznie do **strtof —**. Dla obu funkcji **errno** ustawiono **ERANGE** Jeśli występuje przepełnienie lub niedopełnienie i wywołany nieprawidłowy parametr uchwytu, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md).

Aby uzyskać więcej informacji na temat kodów powrotnych, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Każda funkcja konwertuje ciąg wejściowy *strSource* do **float**. **Strtof —** funkcji konwertuje *strSource* wartości pojedynczej precyzji. **strtof —** przestaje odczytywać ciąg *strSource* przy pierwszym znaku, nie może rozpoznać jako elementu liczby. Może to być kończący znak null. **wcstof —** to wersja znaku dwubajtowego **strtof —**; jej *strSource* argumentu jest ciągiem znaku dwubajtowego. W przeciwnym wypadku te funkcje zachowują się identycznie.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstof**|**strtof**|**strtof**|**wcstof**|
|**_tcstof_l**|**_strtof_l**|**_strtof_l**|**_wcstof_l**|

**LC_NUMERIC** ustawienie kategorii bieżących ustawień regionalnych określa rozpoznawanie znaku podstawy w parametrze *strSource*; Aby uzyskać więcej informacji, zobacz [setlocale, _wsetlocale](setlocale-wsetlocale.md). Funkcje, które nie mają **_l** sufiksa używa bieżących ustawień regionalnych; mają sufiksem są identyczne, z tą różnicą, że używają w zamian przekazanych ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

Jeśli *endptr* nie **NULL**, wskaźnik znaku, który zatrzymał skanowanie jest przechowywany w lokalizacji, która jest wskazywany przez *endptr*. Jeśli konwersja nie może być wykonywana (nie znaleziono żadnych prawidłowych cyfr lub określono nieprawidłową podstawę), wartość *strSource* znajduje się w lokalizacji, która jest wskazywany przez *endptr*.

**strtof —** oczekuje *strSource* do wskaże ciąg o następującej postaci:

[*odstępu*] [*logowania*] [*cyfr*] [__.__ *cyfr*] [{**e** &#124; **E**} [*logowania*] *cyfr*]

A *odstępu* może składać się ze znaków spacji lub tabulatora, które są ignorowane. *logowania* jest plus (**+**) lub minus (**-**); i *cyfr* są co najmniej jedna cyfra dziesiętna. Jeśli żadna cyfra pojawia się przed znakiem podstawy, co najmniej jedna musi występować po znaku podstawy. Cyfr dziesiętnych może następować wykładnik, który składa się z litery wprowadzającej (**e** lub **E**) i opcjonalnie podpisanej liczby całkowitej. Jeśli wykładnik ani znak podstawy nie pojawia się, znak podstawy zakłada się, że ostatniej cyfrze w ciągu. Pierwszy znak, który nie mieści się tym formularzu zatrzymuje skanowanie.

UCRT wersje tych funkcji nie obsługują konwersję Fortran stylu (**d** lub **D**) litery wykładnika. To rozszerzenie niestandardowe była obsługiwana przez wcześniejsze wersje CRT i może być istotnej zmiany w kodzie.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**strtof**, **_strtof_l**|C: \<stdlib.h > C++: &lt;cstdlib — > lub \<stdlib.h >|
|**wcstof**, **_wcstof_l**|C: \<stdlib.h> or \<wchar.h> C++: &lt;cstdlib>, \<stdlib.h> or \<wchar.h>|

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
