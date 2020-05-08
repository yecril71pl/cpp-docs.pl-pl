---
title: _mbctombb, _mbctombb_l
ms.date: 4/2/2020
api_name:
- _mbctombb_l
- _mbctombb
- _o__mbctombb
- _o__mbctombb_l
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
- _mbctombb_l
- _mbctombb
- mbctombb_l
- mbctombb
helpviewer_keywords:
- _mbctombb function
- mbctombb_l function
- mbctombb function
- _mbctombb_l function
ms.assetid: d90970b8-71ff-4586-b6a2-f9ceb811f776
ms.openlocfilehash: d5fcae2a0e403d75383e2998b1ea127dd6f2ef89
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82914269"
---
# <a name="_mbctombb-_mbctombb_l"></a>_mbctombb, _mbctombb_l

Konwertuje dwubajtowy znak wieloznaczny do odpowiadającego jednobajtowego znaku w bajtach.

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
unsigned int _mbctombb(
   unsigned int c
);
unsigned int _mbctombb_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*s*<br/>
Znak wielobajtowy do przekonwertowania.

*locale*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Jeśli się powiedzie, **_mbctombb** i **_mbctombb_l** zwraca znak jednobajtowy, który odpowiada *c*; w przeciwnym razie zwraca *c*.

## <a name="remarks"></a>Uwagi

Funkcje **_mbctombb** i **_mbctombb_l** konwertują dane danego znaku wielobajtowego na odpowiedni jednobajtowy znak wieloznaczny. Znaki muszą odpowiadać znaki jednobajtowe w zakresie 0x20-0x7E lub 0xA1-0xDF do przekonwertowania.

Wartość wyjściowa jest zależna od ustawienia ustawienia kategorii **LC_CTYPE** ustawień regionalnych; Aby uzyskać więcej informacji, zobacz [setlocals](setlocale-wsetlocale.md) . Wersja tej funkcji bez sufiksu **_l** używa bieżących ustawień regionalnych dla tego zachowania zależnego od ustawień regionalnych. wersja z sufiksem **_l** jest identyczna, z tą różnicą, że zamiast tego używa parametru ustawień regionalnych przekazaną. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

W poprzednich wersjach **_mbctombb** został wywołany **zentohan**. Zamiast tego użyj **_mbctombb** .

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_mbctombb**|\<mbstring. h>|
|**_mbctombb_l**|\<mbstring. h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[_mbbtombc, _mbbtombc_l](mbbtombc-mbbtombc-l.md)<br/>
[_mbcjistojms, _mbcjistojms_l, _mbcjmstojis, _mbcjmstojis_l](mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)<br/>
[_mbctohira, _mbctohira_l, _mbctokata, _mbctokata_l](mbctohira-mbctohira-l-mbctokata-mbctokata-l.md)<br/>
[_mbctolower, _mbctolower_l, _mbctoupper, _mbctoupper_l](mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)<br/>
