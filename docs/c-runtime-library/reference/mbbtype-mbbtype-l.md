---
title: _mbbtype, _mbbtype_l
ms.date: 11/04/2016
apiname:
- _mbbtype
- _mbbtype_l
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
- _mbbtype_l
- mbbtype
- mbbtype_l
- _mbbtype
helpviewer_keywords:
- _mbbtype function
- _mbbtype_l function
- mbbtype function
- mbbtype_l function
ms.assetid: b8e34b40-842a-4298-aa39-0bd2d8e51c2a
ms.openlocfilehash: a6d17b99e4314c2ab836a16129ab8a0e6ac7720e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50467174"
---
# <a name="mbbtype-mbbtypel"></a>_mbbtype, _mbbtype_l

Zwraca wartość typu byte, oparte na poprzednich bajtowych.

> [!IMPORTANT]
> Tego API nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
int _mbbtype(
   unsigned char c,
   int type
);
int _mbbtype_l(
   unsigned char c,
   int type,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*c*<br/>
Znak do testowania.

*Typ*<br/>
Typu bajtu do testowania.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

**_mbbtype —** zwraca typ bajtu w ciągu. Ta decyzja zależy kontekstowej, określony przez wartość *typu*, zapewniającą warunku testowego kontroli. *Typ* jest typem poprzednich bajtowych w ciągu. Stałe manifestu w poniższej tabeli są zdefiniowane w Mbctype.h.

|Wartość atrybutu *typu*|**_mbbtype —** testów|Wartość zwracana|*c*|
|---------------------|--------------------------|------------------|---------|
|Dowolna wartość, z wyjątkiem 1|Nieprawidłowy bajt pojedynczy lub bajt|**_MBC_SINGLE** (0)|Jednobajtowych (0x20 — 0x7E, 0xA1 - 0xDF)|
|Dowolna wartość, z wyjątkiem 1|Nieprawidłowy bajt pojedynczy lub bajt|**_MBC_LEAD** (1)|Bajt znaku wielobajtowego (0x81 - 0x9F, 0xE0 — 0xFC)|
|Dowolna wartość, z wyjątkiem 1|Nieprawidłowy bajt jednobajtowych lub potencjalnych klientów|**_MBC_ILLEGAL**<br /><br /> ( -1)|Nieprawidłowy znak (wszystkie wartości z wyjątkiem 0x20 — 0x7E, 0xA1 - 0xDF, 0x81 - 0x9F, 0xE0 — 0xFC|
|1|Nieprawidłowy bajt.|**_MBC_TRAIL** (2)|Końcowe bajt znaku wielobajtowego (0x40 - 0x7E, 0x80 - 0xFC)|
|1|Nieprawidłowy bajt.|**_MBC_ILLEGAL**<br /><br /> ( -1)|Nieprawidłowy znak (wszystkie wartości z wyjątkiem 0x20 — 0x7E, 0xA1 - 0xDF, 0x81 - 0x9F, 0xE0 — 0xFC|

## <a name="remarks"></a>Uwagi

**_Mbbtype —** funkcja określa typ bajtu w znaku wielobajtowego. Jeśli wartość *typu* oznacza dowolną wartość z wyjątkiem 1, **_mbbtype —** testy prawidłowe jednobajtowych lub nie stanowić bajt znaku wielobajtowego. Jeśli wartość *typu* wynosi 1, **_mbbtype —** testów dla nieprawidłowy bajt znaku wielobajtowego.

Wartość wyjściowa jest zależna od ustawienia **LC_CTYPE** ustawienia kategorii ustawień regionalnych; zobacz [setlocale, _wsetlocale](setlocale-wsetlocale.md) Aby uzyskać więcej informacji. **_Mbbtype —** wersja tej funkcji używa bieżących ustawień regionalnych dla wszelkich zachowań; **_mbbtype_l —** wersja jest identyczna, z tą różnicą, że korzysta z parametru ustawień regionalnych, który jest przekazywany zamiast tego . Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

We wcześniejszych wersjach **_mbbtype —** nosiła nazwę **chkctype**. W przypadku nowego kodu użyj **_mbbtype —** zamiast tego.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|---------------------|
|**_mbbtype**|\<mbstring.h>|\<mbctype.h>*|
|**_mbbtype_l**|\<mbstring.h>|\<mbctype.h>*|

\* Aby uzyskać definicje stałych manifestu używanych jako wartości zwracane.

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Klasyfikacja bajtów](../../c-runtime-library/byte-classification.md)<br/>
