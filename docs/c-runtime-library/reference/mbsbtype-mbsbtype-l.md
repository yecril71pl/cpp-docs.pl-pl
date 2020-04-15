---
title: _mbsbtype, _mbsbtype_l
ms.date: 4/2/2020
api_name:
- _mbsbtype_l
- _mbsbtype
- _o__mbsbtype
- _o__mbsbtype_l
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
- mbsbtype
- mbsbtype_l
- _mbsbtype_l
- _mbsbtype
helpviewer_keywords:
- _mbsbtype function
- mbsbtype function
- _mbsbtype_l function
- mbsbtype_l function
ms.assetid: 0d5dd91a-d32d-4f98-ac57-98dfc9e98eac
ms.openlocfilehash: d71a061d9af5028c9bc6b4008f9904606a233592
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81340876"
---
# <a name="_mbsbtype-_mbsbtype_l"></a>_mbsbtype, _mbsbtype_l

Zwraca typ bajtu w ciągu.

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobjęte w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
int _mbsbtype(
   const unsigned char *mbstr,
   size_t count
);
int _mbsbtype_l(
   const unsigned char *mbstr,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*mbstr*<br/>
Adres sekwencji znaków wielobajtowych.

*Liczba*<br/>
Przesunięcie bajtów od głowy ciągu.

*Ustawień regionalnych*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

**_mbsbtype** i **_mbsbtype_l** zwraca wartość całkowitą wskazującą wynik testu na określonym bajcie. Stałe manifestu w poniższej tabeli są zdefiniowane w Mbctype.h.

|Wartość zwracana|Typ bajtów|
|------------------|---------------|
|**_MBC_SINGLE** (0)|Znak jedno bajtowy. Na przykład na stronie kodowej 932 **_mbsbtype** zwraca wartość 0, jeśli określony bajt mieści się w zakresie 0x20 - 0x7E lub 0xA1 - 0xDF.|
|**_MBC_LEAD** (1)|Bajt wiodący o znaku wielobajtowym. Na przykład na stronie kodowej 932 **_mbsbtype** zwraca 1, jeśli określony bajt mieści się w zakresie 0x81 - 0x9F lub 0xE0 - 0xFC.|
|**_MBC_TRAIL** (2)|Bajt spływowy postaci wielobajtowej. Na przykład na stronie kodowej 932 **_mbsbtype** zwraca wartość 2, jeśli określony bajt mieści się w zakresie 0x40 - 0x7E lub 0x80 - 0xFC.|
|**_MBC_ILLEGAL** (-1)|**Ciąg NULL,** nieprawidłowy znak lub bajt zerowy znaleziony przed bajtem przy *liczbie przesunięć* w *mbstr*.|

## <a name="remarks"></a>Uwagi

Funkcja **_mbsbtype** określa typ bajtu w wielobajtowym ciągu znaków. Funkcja sprawdza tylko bajt przy *liczbie* odsunięć w *mbstr,* ignorując nieprawidłowe znaki przed określonym bajtem.

Na wartość wyjściową ma wpływ ustawienie **LC_CTYPE** kategorii ustawień regionalnych; zobacz [setlocale,](setlocale-wsetlocale.md) aby uzyskać więcej informacji. Wersja tej funkcji bez sufiksu **_l** używa bieżących ustawień regionalnych dla tego zachowania zależnego od ustawień regionalnych; wersja z sufiksem **_l** jest identyczna, z tą różnicą, że zamiast tego używa parametru ustawień regionalnych przekazanych. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

Jeśli ciąg wejściowy ma **wartość NULL**, wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w programie [Sprawdzanie poprawności parametrów.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, **errno** jest ustawiona na **EINVAL** i funkcja zwraca **_MBC_ILLEGAL**.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalny nagłówek|
|-------------|---------------------|---------------------|
|**_mbsbtype**|\<mbstring.h>|\<mbctype.h>*|
|**_mbsbtype_l**|\<mbstring.h>|\<mbctype.h>*|

\*Dla stałych manifestu używane jako wartości zwracane.

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Klasyfikacja bajtów](../../c-runtime-library/byte-classification.md)<br/>
