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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 4afd1c92930fe622eb03569913b264d6c285dcda
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341011"
---
# <a name="_mbctombb-_mbctombb_l"></a>_mbctombb, _mbctombb_l

Konwertuje znak wielobajtowy o podwójnym bajecie na odpowiedni jednobajtowy znak wielobajtowy.

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobjęte w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*C*<br/>
Znak wielobajtowy do konwersji.

*Ustawień regionalnych*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Jeśli się powiedzie, **_mbctombb** i **_mbctombb_l** zwraca znak jedno bajtowy odpowiadający *c*; w przeciwnym razie zwraca *c*.

## <a name="remarks"></a>Uwagi

Funkcje **_mbctombb** i **_mbctombb_l** konwertują dany znak wielobajtowy na odpowiedni jednobajtowy znak wielobajtowy. Znaki muszą odpowiadać znakom jedno bajtowym w zakresie 0x20 - 0x7E lub 0xA1 - 0xDF do konwersji.

Na wartość wyjściową ma wpływ ustawienie **LC_CTYPE** kategorii ustawień regionalnych; zobacz [setlocale,](setlocale-wsetlocale.md) aby uzyskać więcej informacji. Wersja tej funkcji bez sufiksu **_l** używa bieżących ustawień regionalnych dla tego zachowania zależnego od ustawień regionalnych; wersja z sufiksem **_l** jest identyczna, z tą różnicą, że zamiast tego używa parametru ustawień regionalnych przekazanych. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

W poprzednich wersjach **_mbctombb** nazywano **zentohan**. Zamiast **tego użyj _mbctombb.**

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_mbctombb**|\<mbstring.h>|
|**_mbctombb_l**|\<mbstring.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[_mbbtombc, _mbbtombc_l](mbbtombc-mbbtombc-l.md)<br/>
[_mbcjistojms, _mbcjistojms_l, _mbcjmstojis, _mbcjmstojis_l](mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)<br/>
[_mbctohira, _mbctohira_l, _mbctokata, _mbctokata_l](mbctohira-mbctohira-l-mbctokata-mbctokata-l.md)<br/>
[_mbctolower, _mbctolower_l, _mbctoupper, _mbctoupper_l](mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)<br/>
