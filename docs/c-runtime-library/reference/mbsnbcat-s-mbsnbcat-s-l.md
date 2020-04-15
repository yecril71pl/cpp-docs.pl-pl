---
title: _mbsnbcat_s, _mbsnbcat_s_l
ms.date: 4/2/2020
api_name:
- _mbsnbcat_s_l
- _mbsnbcat_s
- _o__mbsnbcat_s
- _o__mbsnbcat_s_l
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: b4a9540025ad039458203eec1cc950187b6316a4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81340785"
---
# <a name="_mbsnbcat_s-_mbsnbcat_s_l"></a>_mbsnbcat_s, _mbsnbcat_s_l

Dołącza do wielobajtowego ciągu znaków, co najwyżej pierwsze **n** bajtów innego ciągu znaków wielobajtowych. Są to wersje [_mbsnbcat, _mbsnbcat_l,](mbsnbcat-mbsnbcat-l.md) które mają ulepszenia zabezpieczeń, zgodnie z opisem w [funkcji zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobjęte w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*Dest*<br/>
Ciąg docelowy znaków z końców zerowych z wielobajtowym znakiem docelowym.

*rozmiarWzdjęty*<br/>
Rozmiar buforu *dest* w bajtach.

*src*<br/>
Ciąg źródłowy wielobajtowy znak zakończony z wartością null.

*Liczba*<br/>
Liczba bajtów od *src* do dołączyć do *dest*.

*Ustawień regionalnych*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Zero, jeśli się powiedzie; w przeciwnym razie kod błędu.

### <a name="error-conditions"></a>Warunki błędu

|**Dest**|*rozmiarWzdjęty*|*src*|Wartość zwracana|
|------------|-------------------|-----------|------------------|
|**Null**|Wszelki|Wszelki|**Einval**|
|Dowolne|<= 0|Wszelki|**Einval**|
|Dowolne|Wszelki|**Null**|**Einval**|

Jeśli wystąpi którykolwiek z warunków błędu, funkcja generuje nieprawidłowy błąd parametru, zgodnie z opisem w [weryfikacji parametrów](../../c-runtime-library/parameter-validation.md). Jeśli błąd jest obsługiwany, funkcja zwraca **wartość EINVAL** i ustawia **errno** na **EINVAL**.

## <a name="remarks"></a>Uwagi

Funkcja **_mbsnbcat_s** dołącza do *dest*, co najwyżej, pierwszy *bajtów zliczania* *src*. Jeśli bajt, który bezpośrednio poprzedza znak null w *dest* jest bajtem wiodącym, jest zastępowany przez początkowy bajt *src*. W przeciwnym razie początkowy bajt *src* zastępuje kończący się znak zerowy *dest*. Jeśli w *src* pojawi się bajt zerowy przed dołączeniem bajtów *zliczania,* **_mbsnbcat_s** dołącza wszystkie bajty od *src*, aż do znaku null. Jeśli *liczba* jest większa niż długość *src*, długość *src* jest używana zamiast *liczyć*. Wynikowy ciąg jest zakończony znakiem zerowym. Jeśli kopiowanie odbywa się między ciągami, które nakładają się na siebie, zachowanie jest niezdefiniowane.

Na wartość wyjściową ma wpływ ustawienie **LC_CTYPE** kategorii ustawień regionalnych; zobacz [setlocale, _wsetlocale aby](setlocale-wsetlocale.md) uzyskać więcej informacji. Wersje tych funkcji są identyczne, z tą różnicą, że te, które nie mają **sufiksu _l** używają bieżących ustawień regionalnych, a te, które mają sufiks **_l** zamiast tego używają parametru ustawień regionalnych, który jest przekazywany. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

W języku C++ korzystanie z tych funkcji jest uproszczone przez przeciążenia szablonu; przeciążenia można wywnioskować długość buforu automatycznie, a tym samym wyeliminować konieczność określenia argumentu rozmiaru i mogą automatycznie używać nowszych, bezpieczniejszych funkcji, aby zastąpić starsze, mniej bezpieczne funkcje. Aby uzyskać więcej informacji, zobacz [Bezpieczne przeciążenia szablonu](../../c-runtime-library/secure-template-overloads.md).

Wersje biblioteki debugowania tych funkcji najpierw wypełniają bufor 0xFE. Aby wyłączyć to zachowanie, użyj [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsncat**|[strncat](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)|**_mbsnbcat_s**|[wcsncat](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)|
|**_tcsncat_s_l**|**_strncat_s_l**|**_mbsnbcat_s_l**|**_wcsncat_s_l**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_mbsnbcat_s**|\<mbstring.h>|
|**_mbsnbcat_s_l**|\<mbstring.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Manipulowanie ciągami](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_strncnt, _wcsncnt, _mbsnbcnt, _mbsnbcnt_l, _mbsnccnt, _mbsnccnt_l](strncnt-wcsncnt-mbsnbcnt-mbsnbcnt-l-mbsnccnt-mbsnccnt-l.md)<br/>
[_mbsnbcpy, _mbsnbcpy_l](mbsnbcpy-mbsnbcpy-l.md)<br/>
[_mbsnbcpy_s, _mbsnbcpy_s_l](mbsnbcpy-s-mbsnbcpy-s-l.md)<br/>
[_mbsnbset, _mbsnbset_l](mbsnbset-mbsnbset-l.md)<br/>
[strncat, _strncat_l, wcsncat, _wcsncat_l, _mbsncat, _mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncat_s, _strncat_s_l, wcsncat_s, _wcsncat_s_l, _mbsncat_s, _mbsncat_s_l](strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md)<br/>
