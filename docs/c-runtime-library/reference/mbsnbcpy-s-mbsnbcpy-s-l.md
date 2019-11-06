---
title: _mbsnbcpy_s, _mbsnbcpy_s_l
ms.date: 11/04/2016
api_name:
- _mbsnbcpy_s_l
- _mbsnbcpy_s
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbsnbcpy_s_l
- _mbsnbcpy_s
- mbsnbcpy_s
- _mbsnbcpy_s_l
helpviewer_keywords:
- _mbsnbcpy_s function
- tcsncpy_s function
- mbsnbcpy_s_l function
- _tcsncpy_s_l function
- mbsnbcpy_s function
- tcsncpy_s_l function
- _mbsnbcpy_s_l function
- _tcsncpy_s function
ms.assetid: dfff64ab-fe6f-49c4-99ba-75014e2b0cd6
ms.openlocfilehash: fbbdbeb671f501974ceee9565b8d668e8281f92e
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2019
ms.locfileid: "73624308"
---
# <a name="_mbsnbcpy_s-_mbsnbcpy_s_l"></a>_mbsnbcpy_s, _mbsnbcpy_s_l

Kopiuje **n** bajtów ciągu do ciągu docelowego. Te wersje programu [_mbsnbcpy _mbsnbcpy_l](mbsnbcpy-mbsnbcpy-l.md) mają ulepszenia zabezpieczeń, zgodnie z opisem w temacie [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
errno_t _mbsnbcpy_s(
   unsigned char * strDest,
   size_t sizeInBytes,
   const unsigned char * strSource,
   size_t count
);
errno_t _mbsnbcpy_s_l(
   unsigned char * strDest,
   size_t sizeInBytes,
   const unsigned char * strSource,
   size_t count,
   _locale_t locale
);
template <size_t size>
errno_t _mbsnbcpy_s(
   unsigned char (&strDest)[size],
   const unsigned char * strSource,
   size_t count
); // C++ only
template <size_t size>
errno_t _mbsnbcpy_s_l(
   unsigned char (&strDest)[size],
   const unsigned char * strSource,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parametry

*strDest*<br/>
Miejsce docelowe dla ciągu znaków, który ma zostać skopiowany.

*sizeInBytes*<br/>
Rozmiar buforu docelowego.

*strSource*<br/>
Ciąg znaków, który ma zostać skopiowany.

*liczbą*<br/>
Liczba bajtów do skopiowania.

*ustawienie*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli pomyślne; **EINVAL** , jeśli przekazano zły parametr.

## <a name="remarks"></a>Uwagi

Funkcja **_mbsnbcpy_s** kopiuje *liczbę* bajtów z *strSource* do *strDest*. Jeśli *licznik* przekracza rozmiar *strDest*, jeden z ciągów wejściowych jest wskaźnikiem o wartości null lub *sizeInBytes* lub *Count* ma wartość 0, funkcja wywołuje procedurę obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md) . Jeśli wykonanie może być kontynuowane, funkcja zwraca **EINVAL**. Jeśli parametry źródłowe i docelowe nakładają się na siebie, zachowanie **_mbsnbcpy_s** jest niezdefiniowane.

Wartość wyjściowa jest zależna od ustawienia **LC_CTYPE** kategorii ustawień regionalnych; Aby uzyskać więcej informacji, zobacz [setlocals](setlocale-wsetlocale.md) . Wersje tych funkcji bez sufiksu **_l** używają bieżących ustawień regionalnych dla tego zachowania zależnego od ustawień regionalnych. wersje z sufiksem **_l** są identyczne, z tą różnicą, że w zamian korzystają z przekazaną parametrem ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

> [!NOTE]
> W przeciwieństwie do niezabezpieczonej wersji tej funkcji, **_mbsnbcpy_s** nie wykonuje żadnych dopełnień null i zawsze wartość null kończy ciąg.

W C++programie korzystanie z tych funkcji jest uproszczone przez przeciążenia szablonów; przeciążenia mogą automatycznie wywnioskować długość buforu (eliminując konieczność określenia argumentu rozmiaru) i mogą automatycznie zastąpić starsze, niezabezpieczone funkcje z ich nowszymi, bezpiecznymi odpowiednikami. Aby uzyskać więcej informacji, zobacz [bezpieczne przeciążenia szablonów](../../c-runtime-library/secure-template-overloads.md).

Wersje biblioteki debugowania tych funkcji najpierw wypełniają bufor 0xFE. Aby wyłączyć to zachowanie, użyj [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsncpy_s**|**_strncpy_s**|**_mbsnbcpy_s**|**_wcsncpy_s**|
|**_tcsncpy_s_l**|**_strncpy_s_l**|**_mbsnbcpy_s_l**|**_wcsncpy_s_l**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_mbsnbcpy_s**|\<mbstring. h >|
|**_mbsnbcpy_s_l**|\<mbstring. h >|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_strncnt, _wcsncnt, _mbsnbcnt, _mbsnbcnt_l, _mbsnccnt, _mbsnccnt_l](strncnt-wcsncnt-mbsnbcnt-mbsnbcnt-l-mbsnccnt-mbsnccnt-l.md)<br/>
[_mbsnbicmp, _mbsnbicmp_l](mbsnbicmp-mbsnbicmp-l.md)<br/>
[_mbsnbset, _mbsnbset_l](mbsnbset-mbsnbset-l.md)<br/>
[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
