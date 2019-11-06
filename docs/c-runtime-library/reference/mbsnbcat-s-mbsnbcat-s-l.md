---
title: _mbsnbcat_s, _mbsnbcat_s_l
ms.date: 11/04/2016
api_name:
- _mbsnbcat_s_l
- _mbsnbcat_s
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
- _mbsnbcat_s
- mbsnbcat_s
- _mbsnbcat_s_l
- mbsnbcat_s_l
helpviewer_keywords:
- _tcsncat function
- mbsnbcat_s function
- _mbsnbcat_s function
- _mbsnbcat_s_l function
- _tcsncat_s_l function
- tcsncat_s_l function
- mbsnbcat_s_l function
- tcsncat function
ms.assetid: 2c9e9be7-d979-4a54-8ada-23428b6648a9
ms.openlocfilehash: a148f4be503ee793e4e36855233edfc8fa8f165a
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2019
ms.locfileid: "73624333"
---
# <a name="_mbsnbcat_s-_mbsnbcat_s_l"></a>_mbsnbcat_s, _mbsnbcat_s_l

Dołącza do ciągu znaków wielobajtowych, co najwyżej, pierwsze **n** bajtów innego ciągu znaków wielobajtowych. Są to wersje [_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md) , które mają ulepszenia zabezpieczeń, zgodnie z opisem w temacie [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
errno_t _mbsnbcat_s(
   unsigned char *dest,
   size_t sizeInBytes,
   const unsigned char *src,
   size_t count
);
errno_t _mbsnbcat_s_l(
   unsigned char *dest,
   size_t sizeInBytes,
   const unsigned char *src,
   size_t count,
   _locale_t locale
);
template <size_t size>
errno_t _mbsnbcat_s(
   unsigned char (&dest)[size],
   const unsigned char *src,
   size_t count
); // C++ only
template <size_t size>
errno_t _mbsnbcat_s_l(
   unsigned char (&dest)[size],
   const unsigned char *src,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parametry

*dest*<br/>
Przerwany ciąg znaków wielobajtowych zakończony wartością null.

*sizeInBytes*<br/>
Rozmiar buforu *docelowego* w bajtach.

*SRC*<br/>
Ciąg źródłowy znaku wielobajtowego zakończony wartością null.

*liczbą*<br/>
Liczba bajtów z elementu *src* do dołączenia do miejsca *docelowego*.

*ustawienie*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli pomyślne; w przeciwnym razie kod błędu.

### <a name="error-conditions"></a>Warunki błędów

|**Dest**|*sizeInBytes*|*SRC*|Wartość zwracana|
|------------|-------------------|-----------|------------------|
|**NULL**|Ile|Ile|**EINVAL**|
|Ile|< = 0|Ile|**EINVAL**|
|Ile|Ile|**NULL**|**EINVAL**|

Jeśli wystąpi którykolwiek z warunków błędów, funkcja generuje błąd nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli błąd jest obsługiwany, funkcja zwraca **EINVAL** i ustawia **errno** na **EINVAL**.

## <a name="remarks"></a>Uwagi

Funkcja **_mbsnbcat_s** jest dołączana do miejsca *docelowego*, co najwyżej w pierwszej *liczbie* bajtów *src*. Jeśli bajt, który bezpośrednio poprzedza znak null w polu *docelowy* jest bajtem wiodącym, jest zastępowany przez początkowy bajt *src*. W przeciwnym razie początkowy bajt *src* zastępuje kończący znak null jako *docelowy*. Jeśli bajt o wartości null jest wyświetlany w elemencie *src* przed dołączeniem *liczby* bajtów, **_mbsnbcat_s** dołącza wszystkie bajty z elementu *src*, do znaku null. Jeśli *Liczba* jest większa niż długość elementu *src*, Długość elementu *src* jest używana zamiast *liczby*. Ciąg otrzymany jest zakończony znakiem null. Jeśli kopiowanie odbywa się między nakładającymi się ciągami, zachowanie jest niezdefiniowane.

Wartość wyjściowa jest zależna od ustawienia **LC_CTYPE** kategorii ustawień regionalnych; Zobacz [setlocaling, _wsetlocale,](setlocale-wsetlocale.md) Aby uzyskać więcej informacji. Wersje tych funkcji są identyczne, z tą różnicą, że te, które nie mają sufiksu **_l** , używają bieżących ustawień regionalnych, a te, które mają sufiks **_l** , zamiast tego używają parametru ustawień regionalnych, który został przesłany. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

W C++programie korzystanie z tych funkcji jest uproszczone przez przeciążenia szablonów; przeciążenia mogą automatycznie wywnioskować długość buforu, a tym samym wyeliminować konieczność określenia argumentu rozmiaru i mogą automatycznie korzystać z nowych funkcji, które zastępują starsze, mniej bezpieczne funkcje. Aby uzyskać więcej informacji, zobacz [bezpieczne przeciążenia szablonów](../../c-runtime-library/secure-template-overloads.md).

Wersje biblioteki debugowania tych funkcji najpierw wypełniają bufor 0xFE. Aby wyłączyć to zachowanie, użyj [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsncat**|[strncat](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)|**_mbsnbcat_s**|[wcsncat](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)|
|**_tcsncat_s_l**|**_strncat_s_l**|**_mbsnbcat_s_l**|**_wcsncat_s_l**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_mbsnbcat_s**|\<mbstring. h >|
|**_mbsnbcat_s_l**|\<mbstring. h >|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_strncnt, _wcsncnt, _mbsnbcnt, _mbsnbcnt_l, _mbsnccnt, _mbsnccnt_l](strncnt-wcsncnt-mbsnbcnt-mbsnbcnt-l-mbsnccnt-mbsnccnt-l.md)<br/>
[_mbsnbcpy, _mbsnbcpy_l](mbsnbcpy-mbsnbcpy-l.md)<br/>
[_mbsnbcpy_s, _mbsnbcpy_s_l](mbsnbcpy-s-mbsnbcpy-s-l.md)<br/>
[_mbsnbset, _mbsnbset_l](mbsnbset-mbsnbset-l.md)<br/>
[strncat, _strncat_l, wcsncat, _wcsncat_l, _mbsncat, _mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncat_s, _strncat_s_l, wcsncat_s, _wcsncat_s_l, _mbsncat_s, _mbsncat_s_l](strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md)<br/>
