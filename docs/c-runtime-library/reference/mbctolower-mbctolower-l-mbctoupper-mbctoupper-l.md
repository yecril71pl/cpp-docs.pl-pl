---
title: _mbctolower, _mbctolower_l, _mbctoupper, _mbctoupper_l
ms.date: 4/2/2020
api_name:
- _mbctolower_l
- _mbctoupper_l
- _mbctoupper
- _mbctolower
- _o__mbctolower
- _o__mbctolower_l
- _o__mbctoupper
- _o__mbctoupper_l
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
- mbctoupper_l
- mbctolower_l
- _mbctolower
- _mbctolower_l
- _mbctoupper
- mbctoupper
- mbctolower
- _mbctoupper_l
helpviewer_keywords:
- _mbctolower function
- mbctolower_l function
- totupper function
- _mbctoupper function
- totlower function
- _mbctoupper_l function
- mbctolower function
- _totupper function
- _mbctolower_l function
- mbctoupper_l function
- _totlower function
- mbctoupper function
ms.assetid: 787fab71-3224-4ed7-bc93-4dcd8023fc54
ms.openlocfilehash: 3a3adb32b8620a49110e887788e9f3c4893b6a1a
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82914291"
---
# <a name="_mbctolower-_mbctolower_l-_mbctoupper-_mbctoupper_l"></a>_mbctolower, _mbctolower_l, _mbctoupper, _mbctoupper_l

Testuje i konwertuje wielkość liter znaku wielobajtowego.

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
unsigned int _mbctolower(
   unsigned int c
);
unsigned int _mbctolower_l(
   unsigned int c,
   _locale_t locale
);
unsigned int _mbctoupper(
   unsigned int c
);
unsigned int _mbctoupper_l(
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

Każda z tych funkcji zwraca przekonwertowany znak *c*, jeśli jest to możliwe. W przeciwnym razie zwraca znak *c* niezmieniony.

## <a name="remarks"></a>Uwagi

Funkcje testują znak *c* i, jeśli to możliwe, zastosuj jedną z następujących konwersji.

|Procedury|Skonwertowane|
|--------------|--------------|
|**_mbctolower**, **_mbctolower_l**|Znak pisany wielką literą.|
|**_mbctoupper**, **_mbctoupper_l**|Znak małymi literami.|

Wartość wyjściowa jest zależna od ustawienia ustawienia kategorii **LC_CTYPE** ustawień regionalnych; Aby uzyskać więcej informacji, zobacz [setlocals](setlocale-wsetlocale.md) . Wersja tej funkcji bez sufiksu **_l** używa bieżących ustawień regionalnych dla tego zachowania zależnego od ustawień regionalnych. wersja z sufiksem **_l** jest identyczna, z tą różnicą, że używa zamiast tego parametru ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

W poprzednich wersjach **_mbctolower** nosiła **jtolower**, a **_mbctoupper** została wywołana jako **jtoupper**. W przypadku nowego kodu Użyj zamiast nich nowych nazw.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_totlower**|**ToLower**|**_mbctolower**|**towlower**|
|**_totlower_l**|**_tolower_l**|**_mbctolower_l**|**_towlower_t**|
|**_totupper**|**ToUpper**|**_mbctoupper**|**towupper**|
|**_totupper_l**|**toupper_l**|**_mbctoupper_l**|**_towupper_l**|

## <a name="requirements"></a>Wymagania

|Procedury|Wymagany nagłówek|
|--------------|---------------------|
|**_mbctolower**, **_mbctolower_l**|\<mbstring. h>|
|**_mbctoupper**, **_mbctoupper_l**|\<mbstring. h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[_mbbtombc, _mbbtombc_l](mbbtombc-mbbtombc-l.md)<br/>
[_mbcjistojms, _mbcjistojms_l, _mbcjmstojis, _mbcjmstojis_l](mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)<br/>
[_mbctohira, _mbctohira_l, _mbctokata, _mbctokata_l](mbctohira-mbctohira-l-mbctokata-mbctokata-l.md)<br/>
[_mbctombb, _mbctombb_l](mbctombb-mbctombb-l.md)<br/>
