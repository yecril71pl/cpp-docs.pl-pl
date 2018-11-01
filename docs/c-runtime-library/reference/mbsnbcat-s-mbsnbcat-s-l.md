---
title: _mbsnbcat_s, _mbsnbcat_s_l
ms.date: 11/04/2016
apiname:
- _mbsnbcat_s_l
- _mbsnbcat_s
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
apitype: DLLExport
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
ms.openlocfilehash: d7e7a9d121336486e590ca3bd9e3967b02a2df08
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50497337"
---
# <a name="mbsnbcats-mbsnbcatsl"></a>_mbsnbcat_s, _mbsnbcat_s_l

Dołącza do ciągu znaków wielobajtowych co najwyżej, pierwsze **n** bajtów inny ciąg znaków wielobajtowych. Są to wersje [_mbsnbcat —, _mbsnbcat_l —](mbsnbcat-mbsnbcat-l.md) , które mają wzmocnienia zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Tego API nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Ciąg docelowy znaków wielobajtowych przerwany wartością null.

*sizeInBytes*<br/>
Rozmiar *dest* buforu w bajtach.

*src*<br/>
Ciąg źródłowy znaków wielobajtowych przerwany wartością null.

*Liczba*<br/>
Liczba bajtów z *src* do dołączenia do *dest*.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli to się powiedzie; w przeciwnym razie kod błędu.

### <a name="error-conditions"></a>Warunki błędów

|**docelowy**|*sizeInBytes*|*src*|Wartość zwracana|
|------------|-------------------|-----------|------------------|
|**NULL**|Wszystkie|Wszystkie|**EINVAL**|
|Wszystkie|<= 0|Wszystkie|**EINVAL**|
|Wszystkie|Wszystkie|**NULL**|**EINVAL**|

Jeśli występuje którykolwiek z warunków błędów, funkcja generuje błąd nieprawidłowego parametru, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli obsługiwany jest błąd, funkcja zwraca **EINVAL** i ustawia **errno** do **EINVAL**.

## <a name="remarks"></a>Uwagi

**_Mbsnbcat_s —** funkcja dołącza do *dest*, co najwyżej, pierwsze *liczba* bajtów *src*. Jeśli bajt który bezpośrednio poprzedza znak null w *dest* jest bajtem wiodącym, jest on zastąpiony przez bajt początkowy *src*. W przeciwnym razie bajt początkowy *src* zastępuje kończący znak null z *dest*. Jeśli bajt typu null znajduje się w *src* przed *liczba* bajtów są dołączane, **_mbsnbcat_s —** dołącza wszystkie bajty z *src*, do wartości null znak. Jeśli *liczba* jest większa niż długość *src*, długość *src* jest używana zamiast *liczba*. Wynikowy ciąg znaków jest zakończony znakiem null. Jeśli kopiowanie odbywa się między nakładającymi się ciągami, zachowanie jest niezdefiniowane.

Wartość wyjściowa jest zależna od ustawienia **LC_CTYPE** ustawienia kategorii ustawień regionalnych; zobacz [setlocale, _wsetlocale](setlocale-wsetlocale.md) Aby uzyskać więcej informacji. Wersje tych funkcji są identyczne, z tą różnicą, że te, które nie mają **_l** sufiksa używa bieżących ustawień regionalnych i te, które mają **_l** sufiks używają parametru ustawień regionalnych to przekazana. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

W języku C++ korzystania z tych funkcji jest uproszczone przez przeciążania szablonu; przeciążenia mogą automatycznie wywnioskować długość buforu i tym samym wyeliminować konieczność określenia argumentu rozmiaru i ich funkcje nowszymi, bardziej bezpiecznymi mogą automatycznie używać do zastąpić starsze, mniej bezpieczne funkcje. Aby uzyskać więcej informacji, zobacz [Secure przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

Wersje debugowania tych funkcji najpierw wypełniają bufor 0xfd. Aby wyłączyć to zachowanie, użyj [_crtsetdebugfillthreshold —](crtsetdebugfillthreshold.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsncat —**|[strncat](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)|**_mbsnbcat_s**|[wcsncat —](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)|
|**_tcsncat_s_l —**|**_strncat_s_l**|**_mbsnbcat_s_l**|**_wcsncat_s_l**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_mbsnbcat_s**|\<mbstring.h>|
|**_mbsnbcat_s_l**|\<mbstring.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_strncnt, _wcsncnt, _mbsnbcnt, _mbsnbcnt_l, _mbsnccnt, _mbsnccnt_l](strncnt-wcsncnt-mbsnbcnt-mbsnbcnt-l-mbsnccnt-mbsnccnt-l.md)<br/>
[_mbsnbcpy, _mbsnbcpy_l](mbsnbcpy-mbsnbcpy-l.md)<br/>
[_mbsnbcpy_s, _mbsnbcpy_s_l](mbsnbcpy-s-mbsnbcpy-s-l.md)<br/>
[_mbsnbset, _mbsnbset_l](mbsnbset-mbsnbset-l.md)<br/>
[strncat, _strncat_l, wcsncat, _wcsncat_l, _mbsncat, _mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncat_s, _strncat_s_l, wcsncat_s, _wcsncat_s_l, _mbsncat_s, _mbsncat_s_l](strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md)<br/>
