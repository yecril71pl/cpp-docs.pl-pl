---
title: _strlwr_s —, _strlwr_s_l —, _mbslwr_s —, _mbslwr_s_l —, _wcslwr_s —, _wcslwr_s_l — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _strlwr_s_l
- _mbslwr_s_l
- _mbslwr_s
- _wcslwr_s
- _strlwr_s
- _wcslwr_s_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _strlwr_s_l
- _strlwr_s
- mbslwr_s_l
- strlwr_s_l
- _wcslwr_s
- strlwr_s
- mbslwr_s
- _wcslwr_s_l
- wcslwr_s_l
- _tcslwr_s
- _tcslwr_s_l
- _mbslwr_s_l
- wcslwr_s
- _mbslwr_s
dev_langs:
- C++
helpviewer_keywords:
- _tcslwr_s function
- wcslwr_s function
- _mbslwr_s function
- _wcslwr_s function
- strlwr_s_l function
- mbslwr_s_l function
- _strlwr_s function
- string conversion [C++], case
- strlwr_s function
- wcslwr_s_l function
- _tcslwr_s_l function
- mbslwr_s function
- strings [C++], case
- _wcslwr_s_l function
- converting case, CRT functions
- _strlwr_s_l function
- _mbslwr_s_l function
- case, converting
- tcslwr_s function
- tcslwr_s_l function
- strings [C++], converting case
ms.assetid: 4883d31b-bdac-4049-83a1-91dfdeceee79
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 61f3db37a61a30909e8deadee96c3bfbe2c46bb5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32415342"
---
# <a name="strlwrs-strlwrsl-mbslwrs-mbslwrsl-wcslwrs-wcslwrsl"></a>_strlwr_s, _strlwr_s_l, _mbslwr_s, _mbslwr_s_l, _wcslwr_s, _wcslwr_s_l

Konwertuje ciąg na małe litery, używając bieżących ustawień regionalnych lub obiekt ustawień regionalnych, który jest przekazywany w. Te wersje programu [_strlwr —, _wcslwr —, _mbslwr —, _strlwr_l —, _wcslwr_l —, _mbslwr_l —](strlwr-wcslwr-mbslwr-strlwr-l-wcslwr-l-mbslwr-l.md) zostały ulepszone zabezpieczenia, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> **_mbslwr_s —** i **_mbslwr_s_l —** nie można używać w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
errno_t _strlwr_s(
   char *str,
   size_t numberOfElements
);
errno_t _strlwr_s_l(
   char *str,
   size_t numberOfElements,
   _locale_t locale
);
errno_t _mbslwr_s(
   unsigned char *str,
   size_t numberOfElements
);
errno_t _mbslwr_s_l(
   unsigned char *str,
   size_t numberOfElements,
   _locale_t locale
);
errno_t _wcslwr_s(
   wchar_t *str,
   size_t numberOfElements
);
errno_t _wcslwr_s_l(
   wchar_t *str,
   size_t numberOfElements,
   _locale_t locale
);
template <size_t size>
errno_t _strlwr_s(
   char (&str)[size]
); // C++ only
template <size_t size>
errno_t _strlwr_s_l(
   char (&str)[size],
   _locale_t locale
); // C++ only
template <size_t size>
errno_t _mbslwr_s(
   unsigned char (&str)[size]
); // C++ only
template <size_t size>
errno_t _mbslwr_s_l(
   unsigned char (&str)[size],
   _locale_t locale
); // C++ only
template <size_t size>
errno_t _wcslwr_s(
   wchar_t (&str)[size]
); // C++ only
template <size_t size>
errno_t _wcslwr_s_l(
   wchar_t (&str)[size],
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parametry

*str*<br/>
Zerem ciąg do przekonwertowania na małe litery.

*numberOfElements*<br/>
Rozmiar buforu.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Zero w przypadku powodzenia; Kod błędu zera w przypadku awarii.

Te funkcje walidację ich parametrów. Jeśli *str* nie jest prawidłowym ciągiem zerem, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md) . Jeśli jest dozwolone wykonywanie, aby kontynuować, funkcje zwracają **einval —** i ustaw **errno** do **einval —**. Jeśli *numberOfElements* jest mniejsza niż długość ciągu, również w zwracają **einval —** i ustaw **errno** do **einval —**.

## <a name="remarks"></a>Uwagi

**_Strlwr_s —** konwertuje funkcji, w miejscu, wszelkie wielkie litery w *str* na małe litery. **_mbslwr_s —** jest wersja wielu znaków **_strlwr_s —**. **_wcslwr_s —** jest wersja znaków dwubajtowych **_strlwr_s —**.

Wartość wyjściowa jest zagrożony ustawienie **lc_ctype —** ustawienie kategorii ustawień regionalnych; zobacz [setlocale](setlocale-wsetlocale.md) Aby uzyskać więcej informacji. Wersje tych funkcji bez **_l** Użyj sufiksu bieżące ustawienia regionalne tego zachowania zależnych od ustawień regionalnych; wersje z **_l** sufiks są identyczne, z wyjątkiem tego, aby używały parametr ustawień regionalnych Przekazano zamiast tego. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

W języku C++ za pomocą tych funkcji zostało uproszczone dzięki przeciążenia szablonu; przeciążeń można automatycznie rozpoznać długość buforu (wyeliminowanie konieczności określania argumentem rozmiaru) i automatycznie można zastąpić starszą, które nie są bezpieczne funkcje z ich odpowiedniki nowsza, bezpieczne. Aby uzyskać więcej informacji, zobacz [Secure szablonu Overloads](../../c-runtime-library/secure-template-overloads.md).

Wersje tych funkcji do debugowania najpierw wprowadzić bufor 0xFD. Aby wyłączyć to zachowanie, użyj [_crtsetdebugfillthreshold —](crtsetdebugfillthreshold.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcslwr_s —**|**_strlwr_s**|**_mbslwr_s**|**_wcslwr_s**|
|**_tcslwr_s_l —**|**_strlwr_s_l**|**_mbslwr_s_l**|**_wcslwr_s_l**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_strlwr_s —**, **_strlwr_s_l —**|\<string.h>|
|**_mbslwr_s —**, **_mbslwr_s_l —**|\<mbstring.h>|
|**_wcslwr_s —**, **_wcslwr_s_l —**|\<String.h > lub \<wchar.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```cpp
// crt_strlwr_s.cpp
// This program uses _strlwr_s and _strupr_s to create
// uppercase and lowercase copies of a mixed-case string.
//

#include <string.h>
#include <stdio.h>
#include <stdlib.h>

int main()
{
   char str[] = "The String to End All Strings!";
   char *copy1, *copy2;
   errno_t err;

   err = _strlwr_s( copy1 = _strdup(str), strlen(str) + 1);
   err = _strupr_s( copy2 = _strdup(str), strlen(str) + 1);

   printf( "Mixed: %s\n", str );
   printf( "Lower: %s\n", copy1 );
   printf( "Upper: %s\n", copy2 );

   free( copy1 );
   free( copy2 );

   return 0;
}
```

```Output
Mixed: The String to End All Strings!
Lower: the string to end all strings!
Upper: THE STRING TO END ALL STRINGS!
```

## <a name="see-also"></a>Zobacz także

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[Interpretacja wielobajtowych sekwencji znaków](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_strupr_s, _strupr_s_l, _mbsupr_s, _mbsupr_s_l, _wcsupr_s, _wcsupr_s_l](strupr-s-strupr-s-l-mbsupr-s-mbsupr-s-l-wcsupr-s-wcsupr-s-l.md)<br/>
