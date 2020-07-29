---
title: strcpy_s, wcscpy_s, _mbscpy_s, _mbscpy_s_l
ms.date: 5/28/2020
api_name:
- wcscpy_s
- _mbscpy_s
- _mbscpy_s_l
- strcpy_s
- _o__mbscpy_s
- _o__mbscpy_s_l
- _o_strcpy_s
- _o_wcscpy_s
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- strcpy_s
- _mbscpy_s
- _mbscpy_s_l
- _tcscpy_s
- wcscpy_s
helpviewer_keywords:
- strcpy_s function
- _tcscpy_s function
- _mbscpy_s function
- _mbscpy_s_l function
- copying strings
- strings [C++], copying
- tcscpy_s function
- wcscpy_s function
ms.assetid: 611326f3-7929-4a5d-a465-a4683af3b053
ms.openlocfilehash: b2957490dbf045b9a3258a72b6bda0aaf1a38c0f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229301"
---
# <a name="strcpy_s-wcscpy_s-_mbscpy_s-_mbscpy_s_l"></a>strcpy_s, wcscpy_s, _mbscpy_s, _mbscpy_s_l

Kopiuje ciąg. Te wersje [strcpy, wcscpy, _mbscpy](strcpy-wcscpy-mbscpy.md) mają ulepszenia zabezpieczeń, zgodnie z opisem w temacie [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> **_mbscpy_s** i **_mbscpy_s_l** nie mogą być używane w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
errno_t strcpy_s(
   char *dest,
   rsize_t dest_size,
   const char *src
);
errno_t wcscpy_s(
   wchar_t *dest,
   rsize_t dest_size,
   const wchar_t *src
);
errno_t _mbscpy_s(
   unsigned char *dest,
   rsize_t dest_size,
   const unsigned char *src
);
errno_t _mbscpy_s_l(
   unsigned char *dest,
   rsize_t dest_size,
   const unsigned char *src,
   _locale_t locale
);
```

```cpp
// Template functions are C++ only:
template <size_t size>
errno_t strcpy_s(
   char (&dest)[size],
   const char *src
); // C++ only
template <size_t size>
errno_t wcscpy_s(
   wchar_t (&dest)[size],
   const wchar_t *src
); // C++ only
template <size_t size>
errno_t _mbscpy_s(
   unsigned char (&dest)[size],
   const unsigned char *src
); // C++ only
template <size_t size>
errno_t _mbscpy_s_l(
   unsigned char (&dest)[size],
   const unsigned char *src,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parametry

*dest*<br/>
Lokalizacja buforu ciągu docelowego.

*dest_size*<br/>
Rozmiar buforu ciągu docelowego w **`char`** jednostkach dla wąskich i wielobajtowych funkcji oraz **`wchar_t`** jednostek dla szerokich funkcji. Ta wartość musi być większa od zera i nie większa niż **RSIZE_MAX**. Upewnij się, że w tym rozmiarze są używane konta kończące się `NULL` po ciągu.

*src*<br/>
Bufor ciągu źródła zakończony znakiem null.

*ustawienie*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli pomyślne; w przeciwnym razie wystąpi błąd.

### <a name="error-conditions"></a>Warunki błędów

|*dest*|*dest_size*|*src*|Wartość zwracana|Zawartość miejsca *docelowego*|
|----------------------|------------------------|-----------------|------------------|----------------------------------|
|**NULL**|dowolny|dowolny|**EINVAL**|nie zmodyfikowano|
|dowolny|dowolny|**NULL**|**EINVAL**|*cel*[0] ustawiony na 0|
|dowolny|0 lub za mały|dowolny|**ERANGE**|*cel*[0] ustawiony na 0|

## <a name="remarks"></a>Uwagi

Funkcja **strcpy_s** kopiuje zawartość w adresie *src*, łącznie z kończącym znakiem null, do lokalizacji określonej przez obiekt *docelowy*. Ciąg docelowy musi być wystarczająco duży, aby pomieścić ciąg źródłowy i jego kończący znak null. Zachowanie **strcpy_s** jest niezdefiniowane, jeśli parametry źródłowe i docelowe nakładają się na siebie.

**wcscpy_s** jest wersją znaku **strcpy_s**, a **_mbscpy_s** jest wersją znaku wielobajtowego. Argumenty **wcscpy_s** są ciągami znaków dwubajtowych; te **_mbscpy_s** i **_mbscpy_s_l** są ciągami znaków wielobajtowych. Funkcje te zachowują się identycznie w inny sposób. **_mbscpy_s_l** jest taka sama jak **_mbscpy_s** , z tą różnicą, że używa parametru ustawień regionalnych przekazaną zamiast bieżących ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

Jeśli *docelowy* lub *src* jest wskaźnikiem o wartości null lub jeśli rozmiar ciągu docelowego *dest_size* jest zbyt mały, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje zwracają **EINVAL** i ustawiają **errno** na **EINVAL** , gdy element *docelowy* lub *src* jest wskaźnikiem o wartości null i zwracają **ERANGE** i ustawia **errno** na **ERANGE** , gdy ciąg docelowy jest zbyt mały.

Po pomyślnym wykonaniu ciąg docelowy jest zawsze zakończony wartością null.

W języku C++ korzystanie z tych funkcji jest uproszczone przez przeciążenia szablonu, które mogą automatycznie wywnioskować długość buforu, aby nie trzeba było określać argumentu rozmiaru i można automatycznie zastąpić starsze, mniej bezpieczne funkcje z ich nowszymi, bardziej bezpiecznymi odpowiednikami. Aby uzyskać więcej informacji, zobacz [bezpieczne przeciążenia szablonów](../../c-runtime-library/secure-template-overloads.md).

Wersje biblioteki debugowania tych funkcji najpierw wypełniają bufor 0xFE. Aby wyłączyć to zachowanie, użyj [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _MBCS _UNICODE &|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcscpy_s**|**strcpy_s**|**_mbscpy_s**|**wcscpy_s**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**strcpy_s**|\<string.h>|
|**wcscpy_s**|\<string.h> lub \<wchar.h>|
|**_mbscpy_s**|\<mbstring.h>|

Te funkcje są specyficzne dla firmy Microsoft. Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

W przeciwieństwie do kodu jakości produkcyjnej, ten przykład wywołuje funkcje bezpiecznego ciągu bez sprawdzania pod kątem błędów:

```C
// crt_strcpy_s.c
// Compile by using: cl /W4 crt_strcpy_s.c
// This program uses strcpy_s and strcat_s
// to build a phrase.

#include <string.h>     // for strcpy_s, strcat_s
#include <stdlib.h>     // for _countof
#include <stdio.h>      // for printf
#include <errno.h>      // for return values

int main(void)
{
    char string[80];

    strcpy_s(string, _countof(string), "Hello world from ");
    strcat_s(string, _countof(string), "strcpy_s ");
    strcat_s(string, _countof(string), "and ");
    strcat_s(string, _countof(string), "strcat_s!");

    printf("String = %s\n", string);
}
```

```Output
String = Hello world from strcpy_s and strcat_s!
```

W przypadku kompilowania kodu w języku C++ wersje szablonów mogą być łatwiejsze w użyciu.

```cpp
// crt_wcscpy_s.cpp
// Compile by using: cl /EHsc /W4 crt_wcscpy_s.cpp
// This program uses wcscpy_s and wcscat_s
// to build a phrase.

#include <cstring>  // for wcscpy_s, wcscat_s
#include <cstdlib>  // for _countof
#include <iostream> // for cout, includes <cstdlib>, <cstring>
#include <errno.h>  // for return values

int main(void)
{
    wchar_t string[80];
    // using template versions of wcscpy_s and wcscat_s:
    wcscpy_s(string, L"Hello world from ");
    wcscat_s(string, L"wcscpy_s ");
    wcscat_s(string, L"and ");
    // of course we can supply the size explicitly if we want to:
    wcscat_s(string, _countof(string), L"wcscat_s!");

    std::wcout << L"String = " << string << std::endl;
}
```

```Output
String = Hello world from wcscpy_s and wcscat_s!
```

## <a name="see-also"></a>Zobacz także

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md) <br/>
[strcat, wcscat, _mbscat, _mbscat_l](strcat-wcscat-mbscat.md) <br/>
[strcmp, wcscmp, _mbscmp, _mbscmp_l](strcmp-wcscmp-mbscmp.md) <br/>
[strncat_s, _strncat_s_l, wcsncat_s, _wcsncat_s_l, _mbsncat_s, _mbsncat_s_l](strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md) <br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md) <br/>
[strncpy_s, _strncpy_s_l, wcsncpy_s, _wcsncpy_s_l, _mbsncpy_s, _mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md) <br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md) <br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md) <br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
