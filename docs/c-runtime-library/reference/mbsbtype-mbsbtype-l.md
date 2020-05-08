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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: c1431a2d0886ffd3d16b43abf82b7342c166273a
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82909480"
---
# <a name="_mbsbtype-_mbsbtype_l"></a>_mbsbtype, _mbsbtype_l

Zwraca typ Byte w ciągu.

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*liczbą*<br/>
Przesunięcie bajtu od początku ciągu.

*locale*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

**_mbsbtype** i **_mbsbtype_l** zwraca wartość całkowitą wskazującą wynik testu w określonym bajcie. Stałe manifestu w poniższej tabeli są zdefiniowane w Mbctype. h.

|Wartość zwracana|Typ bajtu|
|------------------|---------------|
|**_MBC_SINGLE** (0)|Znak jednobajtowy. Na przykład, na stronie kodowej 932, **_mbsbtype** zwraca wartość 0, jeśli określony bajt znajduje się w zakresie 0X20-0X7E lub 0XA1-0xDF.|
|**_MBC_LEAD** (1)|Bajt wiodący znaku wielobajtowego. Na przykład, na stronie kodowej 932, **_mbsbtype** zwraca wartość 1, jeśli określony bajt znajduje się w zakresie 0X81-0X9F lub wartość 0xE0-0xFC.|
|**_MBC_TRAIL** (2)|Bajt końcowy znaku wielobajtowego. Na przykład, na stronie kodowej 932, **_mbsbtype** zwraca wartość 2, jeśli określony bajt znajduje się w zakresie 0X40-0x7E lub 0X80-0xFC.|
|**_MBC_ILLEGAL** (-1)|Ciąg o **wartości null** , nieprawidłowy znak lub bajt o wartości null znaleziony przed bajtem *z przesunięciami* w *mbstr*.|

## <a name="remarks"></a>Uwagi

Funkcja **_mbsbtype** określa typ bajtu w ciągu znaków wielobajtowych. Funkcja analizuje tylko bajt o *liczbie* przesunięcia w *mbstr*, ignorując nieprawidłowe znaki przed określonym bajtem.

Wartość wyjściowa jest zależna od ustawienia ustawienia kategorii **LC_CTYPE** ustawień regionalnych; Aby uzyskać więcej informacji, zobacz [setlocals](setlocale-wsetlocale.md) . Wersja tej funkcji bez sufiksu **_l** używa bieżących ustawień regionalnych dla tego zachowania zależnego od ustawień regionalnych. wersja z sufiksem **_l** jest identyczna, z tą różnicą, że zamiast tego używa parametru ustawień regionalnych przekazaną. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

Jeśli ciąg wejściowy ma **wartość null**, zostanie wywołana procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **errno** jest ustawiona na **EINVAL** , a funkcja zwraca **_MBC_ILLEGAL**.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalny nagłówek|
|-------------|---------------------|---------------------|
|**_mbsbtype**|\<mbstring. h>|\<Mbctype. h> *|
|**_mbsbtype_l**|\<mbstring. h>|\<Mbctype. h> *|

\*Dla stałych manifestu używanych jako wartości zwracane.

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Klasyfikacja bajtów](../../c-runtime-library/byte-classification.md)<br/>
