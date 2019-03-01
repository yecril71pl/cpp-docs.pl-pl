---
title: strcat, wcscat, _mbscat
ms.date: 11/04/2016
apiname:
- _mbscat
- wcscat
- strcat
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
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- _mbscat
- _ftcscat
- _tcscat
- strcat
- wcscat
helpviewer_keywords:
- concatenating strings
- mbscat function
- _ftcscat function
- _tcscat function
- ftcscat function
- strcat function
- strings [C++], appending
- _mbscat function
- tcscat function
- strings [C++], concatenating
- appending strings
- wcscat function
ms.assetid: c89c4ef1-817a-44ff-a229-fe22d06ba78a
ms.openlocfilehash: 629b66a5c9dded3a910919f5e302a97c4f731240
ms.sourcegitcommit: e06648107065f3dea35f40c1ae5999391087b80b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/01/2019
ms.locfileid: "57210409"
---
# <a name="strcat-wcscat-mbscat"></a>strcat, wcscat, _mbscat

Dołącza ciąg. Bardziej bezpieczne wersje tych funkcji są dostępne; zobacz [strcat_s wcscat_s —, _mbscat_s —](strcat-s-wcscat-s-mbscat-s.md).

> [!IMPORTANT]
> **_mbscat_s —** nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
char *strcat(
   char *strDestination,
   const char *strSource
);
wchar_t *wcscat(
   wchar_t *strDestination,
   const wchar_t *strSource
);
unsigned char *_mbscat(
   unsigned char *strDestination,
   const unsigned char *strSource
);
template <size_t size>
char *strcat(
   char (&strDestination)[size],
   const char *strSource
); // C++ only
template <size_t size>
wchar_t *wcscat(
   wchar_t (&strDestination)[size],
   const wchar_t *strSource
); // C++ only
template <size_t size>
unsigned char *_mbscat(
   unsigned char (&strDestination)[size],
   const unsigned char *strSource
); // C++ only
```

### <a name="parameters"></a>Parametry

*strDestination*<br/>
Ciąg docelowy zakończony wartością null.

*strSource*<br/>
Ciąg źródłowy zakończony wartością null.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca ciąg docelowy (*strDestination*). Zwraca żadnej wartości zarezerwowanej, aby wskazać błąd.

## <a name="remarks"></a>Uwagi

**Strcat —** funkcja dołącza *strSource* do *strDestination* i kończy się wynikowy ciąg znakiem null. Początkowy znak *strSource* zastępuje kończący znak null z *strDestination*. Zachowanie **strcat —** jest niezdefiniowane, jeżeli ciągi źródłowe i docelowe nakładają się.

> [!IMPORTANT]
> Ponieważ **strcat —** nie sprawdza wystarczająco dużo miejsca w *strDestination* przed dołączeniem *strSource*, jest potencjalną przyczyną przekroczenia buforu. Należy rozważyć użycie [strncat —](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md) zamiast tego.

**wcscat —** i **_mbscat —** są wersjami znaków dwubajtowych i znaków wielobajtowych **strcat —**. Argumenty i wartość zwracana przez **wcscat —** są znakami dwubajtowymi ciągów; te z **_mbscat —** są ciągami znaków wielobajtowych. Te trzy funkcje zachowują się identycznie.

W języku C++ funkcje te mają przeciążenia szablonu, które wywołują nowsze, bezpieczne odpowiedniki tych funkcji. Aby uzyskać więcej informacji, zobacz [Secure przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcscat**|**strcat**|**_mbscat**|**wcscat**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**strcat**|\<string.h>|
|**wcscat**|\<Włącz String.h > lub \<wchar.h >|
|**_mbscat**|\<mbstring.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [strcpy](strcpy-wcscpy-mbscpy.md).

## <a name="see-also"></a>Zobacz także

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[strncat, _strncat_l, wcsncat, _wcsncat_l, _mbsncat, _mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
