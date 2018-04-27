---
title: strcpy_s —, wcscpy_s —, _mbscpy_s — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/22/2086
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- wcscpy_s
- _mbscpy_s
- strcpy_s
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
- strcpy_s
- _mbscpy_s
- _tcscpy_s
- wcscpy_s
dev_langs:
- C++
helpviewer_keywords:
- strcpy_s function
- _tcscpy_s function
- _mbscpy_s function
- copying strings
- strings [C++], copying
- tcscpy_s function
- wcscpy_s function
ms.assetid: 611326f3-7929-4a5d-a465-a4683af3b053
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 16dfe0f560097ab7a5a423f7730c215c2d05530f
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="strcpys-wcscpys-mbscpys"></a>strcpy_s, wcscpy_s, _mbscpy_s

Kopiuje ciąg. Te wersje programu [strcpy wcscpy —, _mbscpy —](strcpy-wcscpy-mbscpy.md) zostały ulepszone zabezpieczenia, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> **_mbscpy_s —** nie można używać w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
```

### <a name="parameters"></a>Parametry

*dest*<br/>
Lokalizacja buforu ciągu docelowego.

*dest_size*<br/>
Rozmiar buforu ciągu docelowego w **char** jednostki dla funkcji wąskie i wielobajtowe, i **wchar_t** jednostki dla szerokiego funkcji. Ta wartość musi być większa od zera i nie większą niż **RSIZE_MAX**.

*src*<br/>
Bufor ciąg źródłowy zerem.

## <a name="return-value"></a>Wartość zwracana

Zero w przypadku powodzenia; w przeciwnym razie błąd.

### <a name="error-conditions"></a>Warunki błędów

|*dest*|*dest_size*|*src*|Wartość zwracana|Zawartość *docelowy*|
|----------------------|------------------------|-----------------|------------------|----------------------------------|
|**NULL**|wszystkie|wszystkie|**EINVAL —**|Nie zmodyfikowano|
|wszystkie|wszystkie|**NULL**|**EINVAL —**|*docelowy*zestawu [0] 0|
|wszystkie|0 lub za mały|wszystkie|**ERANGE —**|*docelowy*zestawu [0] 0|

## <a name="remarks"></a>Uwagi

**Strcpy_s —** funkcja kopiuje zawartość adresu *src*, w tym znak końcowy null do lokalizacji określonej przez *dest*. Ciąg docelowego musi być wystarczająco duży, aby pomieścić ciąg źródłowy i jej znak końcowy null. Zachowanie **strcpy_s —** zdefiniowano nakładania się ciągów źródłowych i docelowych.

**wcscpy_s —** jest wersja znaków dwubajtowych **strcpy_s —**, i **_mbscpy_s —** jest wersja znaków wielobajtowych. Argumenty **wcscpy_s —** są znaków dwubajtowych ciągi; tych **_mbscpy_s —** są ciągami znaków wielobajtowych. Te trzy funkcje działają tak samo w przeciwnym razie wartość.

Jeśli *dest* lub *src* jest wskaźnika o wartości null, lub jeśli rozmiar ciągu docelowego *dest_size* jest za mały, zostanie wywołany program obsługi nieprawidłowych parametrów, zgodnie z opisem w [Sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, te funkcje zwracają **einval —** i ustaw **errno** do **einval —** podczas *dest* lub  *SRC* jest wskaźnika o wartości null i zwracają **erange —** i ustaw **errno** do **erange —** po ciągu docelowego jest za mały.

Po pomyślnym wykonaniu ciąg docelowej są jest zawsze zerem.

W języku C++ użycia tych funkcji zostało uproszczone dzięki szablonu przeciążeń, które można wnioskować o długości buforu automatycznie, dzięki czemu nie trzeba określić argument rozmiar i automatycznie można zastąpić starszą funkcji o niższym poziomie zabezpieczeń z ich nowsze bardziej bezpieczne odpowiedniki. Aby uzyskać więcej informacji, zobacz [Secure szablonu Overloads](../../c-runtime-library/secure-template-overloads.md).

Wersje biblioteki debugowania tych funkcji najpierw wprowadzić bufor 0xFE. Aby wyłączyć to zachowanie, użyj [_crtsetdebugfillthreshold —](crtsetdebugfillthreshold.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcscpy_s —**|**strcpy_s**|**_mbscpy_s**|**wcscpy_s**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**strcpy_s**|\<string.h>|
|**wcscpy_s**|\<String.h > lub \<wchar.h >|
|**_mbscpy_s**|\<mbstring.h>|

Te funkcje są specyficzne dla firmy Microsoft. Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

W przeciwieństwie do produkcji jakości kodu w tym przykładzie wywołuje funkcje bezpieczny ciąg bez sprawdzania pod kątem błędów:

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

Podczas kompilowania kodu C++, wersji szablonu może być łatwiejsze do użycia.

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
[strcat, wcscat, _mbscat](strcat-wcscat-mbscat.md) <br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md) <br/>
[strncat_s, _strncat_s_l, wcsncat_s, _wcsncat_s_l, _mbsncat_s, _mbsncat_s_l](strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md) <br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md) <br/>
[strncpy_s, _strncpy_s_l, wcsncpy_s, _wcsncpy_s_l, _mbsncpy_s, _mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md) <br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md) <br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md) <br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
