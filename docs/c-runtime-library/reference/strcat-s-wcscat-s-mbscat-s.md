---
title: strcat_s, wcscat_s, _mbscat_s
ms.date: 11/04/2016
apiname:
- strcat_s
- _mbscat_s
- wcscat_s
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
- strcat_s
- wcscat_s
- _mbscat_s
helpviewer_keywords:
- wcscat_s function
- strcat_s function
- mbscat_s function
- strings [C++], appending
- _mbscat_s function
- appending strings
ms.assetid: 0f2f9901-c5c5-480b-98bc-f8f690792fc0
ms.openlocfilehash: 7b622fbefc690317a4b57e3fd1bb54712b84f2a0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50621315"
---
# <a name="strcats-wcscats-mbscats"></a>strcat_s, wcscat_s, _mbscat_s

Dołącza ciąg. Te wersje [strcat —, wcscat —, _mbscat —](strcat-wcscat-mbscat.md) mają wzmocnienia zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> **_mbscat_s —** nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
errno_t strcat_s(
   char *strDestination,
   size_t numberOfElements,
   const char *strSource
);
errno_t wcscat_s(
   wchar_t *strDestination,
   size_t numberOfElements,
   const wchar_t *strSource
);
errno_t _mbscat_s(
   unsigned char *strDestination,
   size_t numberOfElements,
   const unsigned char *strSource
);
template <size_t size>
errno_t strcat_s(
   char (&strDestination)[size],
   const char *strSource
); // C++ only
template <size_t size>
errno_t wcscat_s(
   wchar_t (&strDestination)[size],
   const wchar_t *strSource
); // C++ only
template <size_t size>
errno_t _mbscat_s(
   unsigned char (&strDestination)[size],
   const unsigned char *strSource
); // C++ only
```

### <a name="parameters"></a>Parametry

*strDestination*<br/>
Bufor ciąg docelowy zakończony wartością null.

*numberOfElements*<br/>
Rozmiar buforu ciągu docelowego.

*strSource*<br/>
Bufor ciągu źródła zakończony znakiem null.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli to się powiedzie; Kod błędu.

### <a name="error-conditions"></a>Warunki błędów

|*strDestination*|*numberOfElements*|*strSource*|Wartość zwracana|Zawartość *strDestination*|
|----------------------|------------------------|-----------------|------------------|----------------------------------|
|**Wartość NULL** lub niezakończony|Wszystkie|Wszystkie|**EINVAL**|Nie zmodyfikowano|
|Wszystkie|Wszystkie|**NULL**|**EINVAL**|*strDestination*[0] ustawiony na 0|
|Wszystkie|0 lub zbyt mały|Wszystkie|**ERANGE**|*strDestination*[0] ustawiony na 0|

## <a name="remarks"></a>Uwagi

**Strcat_s** funkcja dołącza *strSource* do *strDestination* i kończy się wynikowy ciąg znakiem null. Początkowy znak *strSource* zastępuje kończący znak null z *strDestination*. Zachowanie **strcat_s** jest niezdefiniowane, jeżeli ciągi źródłowe i docelowe nakładają się.

Należy pamiętać, że drugi parametr całkowity rozmiar buforu nie pozostały rozmiar:

```C
char buf[16];
strcpy_s(buf, 16, "Start");
strcat_s(buf, 16, " End");               // Correct
strcat_s(buf, 16 - strlen(buf), " End"); // Incorrect
```

**wcscat_s —** i **_mbscat_s —** są wersjami znaków dwubajtowych i znaków wielobajtowych **strcat_s**. Argumenty i wartość zwracana przez **wcscat_s —** są znakami dwubajtowymi ciągów; te z **_mbscat_s —** są ciągami znaków wielobajtowych. Te trzy funkcje zachowują się identycznie.

Jeśli *strDestination* jest wskaźnikiem typu null lub nie jest zakończony znakiem null, lub jeśli *strSource* jest **NULL** wskaźnika, lub jeśli ciąg docelowy jest zbyt mały, nieprawidłowy parametr Program obsługi zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje zwracają **EINVAL** i ustaw **errno** do **EINVAL**.

W języku C++ korzystanie z tych funkcji jest uproszczone przez przeciążania szablonu; przeciążenia mogą automatycznie wywnioskować długość buforu (eliminując potrzebę określenia argumentu rozmiaru) oraz ich mogą automatycznie zastąpić starsze, niezabezpieczone funkcje ich nowsze, bezpieczne odpowiedniki. Aby uzyskać więcej informacji, zobacz [Secure przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

Wersje debugowania tych funkcji najpierw wypełniają bufor 0xfd. Aby wyłączyć to zachowanie, użyj [_crtsetdebugfillthreshold —](crtsetdebugfillthreshold.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcscat_s**|**strcat_s**|**_mbscat_s**|**wcscat_s**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**strcat_s**|\<string.h>|
|**wcscat_s**|\<Włącz String.h > lub \<wchar.h >|
|**_mbscat_s**|\<mbstring.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład kodu w [strcpy_s wcscpy_s —, _mbscpy_s —](strcpy-s-wcscpy-s-mbscpy-s.md).

## <a name="see-also"></a>Zobacz także

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[strncat, _strncat_l, wcsncat, _wcsncat_l, _mbsncat, _mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
