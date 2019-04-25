---
title: _mbbtombc, _mbbtombc_l
ms.date: 11/04/2016
apiname:
- _mbbtombc_l
- _mbbtombc
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
- _mbbtombc_l
- _mbbtombc
- mbbtombc_l
- mbbtombc
helpviewer_keywords:
- mbbtombc_l function
- mbbtombc function
- _mbbtombc_l function
- _mbbtombc function
ms.assetid: 78593389-b0fc-43b6-8c1f-2a6bf702d64e
ms.openlocfilehash: 63b5dd33399201cd6ead7dbd1f710c8bebe53c69
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62156911"
---
# <a name="mbbtombc-mbbtombcl"></a>_mbbtombc, _mbbtombc_l

Konwertuje jednobajtowego znaku wielobajtowego do odpowiedniego znaku wielobajtowego znaków dwubajtowych.

> [!IMPORTANT]
> Tego API nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
unsigned int _mbbtombc(
   unsigned int c
);
unsigned int _mbbtombc_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*c*<br/>
Znak Jednobajtowy, która ma zostać przekształcony.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Jeśli **_mbbtombc —** pomyślnie konwertuje *c*, funkcja zwraca znak wielobajtowy; w przeciwnym razie zwraca *c*.

## <a name="remarks"></a>Uwagi

**_Mbbtombc —** funkcja konwertuje dany znak wielobajtowy pojedynczych bajtów do odpowiedniego znaku wielobajtowego znaków dwubajtowych. Znaki musi być w zakresie 0x20 — 0x7E lub 0xA1 - 0xDF ma zostać przekonwertowany.

Wartość wyjściowa jest zależna od ustawienia **LC_CTYPE** ustawienia kategorii ustawień regionalnych; zobacz [setlocale, _wsetlocale](setlocale-wsetlocale.md) Aby uzyskać więcej informacji. Wersje tej funkcji są identyczne, z tą różnicą, że **_mbbtombc —** używa bieżących ustawień regionalnych dla zachowania zależnego od ustawień regionalnych i **_mbbtombc_l —** zamiast tego używa przekazanego parametru ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

We wcześniejszych wersjach **_mbbtombc —** nosiła nazwę **hantozen**. W przypadku nowego kodu użyj **_mbbtombc —**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_mbbtombc**|\<mbstring.h>|
|**_mbbtombc_l**|\<mbstring.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[_mbctombb, _mbctombb_l](mbctombb-mbctombb-l.md)<br/>
