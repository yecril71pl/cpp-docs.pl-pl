---
title: _mbbtype, _mbbtype_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- _mbbtype function
- _mbbtype_l function
- mbbtype function
- mbbtype_l function
ms.assetid: b8e34b40-842a-4298-aa39-0bd2d8e51c2a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 91b78b0dc57873810f96a793288da3f1457299de
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32404418"
---
# <a name="mbbtype-mbbtypel"></a>_mbbtype, _mbbtype_l

Zwraca typ byte, oparte na poprzednim bajtów.

> [!IMPORTANT]
> Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Typ bajtów do testowania.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

**_mbbtype —** zwraca typ bajtów w ciągu. Ta decyzja jest kontekstowa, określony przez wartość *typu*, zapewniające warunku formantu. *Typ* jest typem poprzedniej bajtów w ciągu. Stałe manifestu w poniższej tabeli są definiowane w Mbctype.h.

|Wartość *typu*|**_mbbtype —** testów dla|Wartość zwracana|*c*|
|---------------------|--------------------------|------------------|---------|
|Wszystkie wartości z wyjątkiem 1|Nieprawidłowa jednobajtowych lub bajtu|**_MBC_SINGLE** (0)|Jednobajtowych (0x20 - 0x7E, 0xA1 - 0xDF)|
|Wszystkie wartości z wyjątkiem 1|Nieprawidłowa jednobajtowych lub bajtu|**_MBC_LEAD** (1)|Prowadzić bajtów znaków wielobajtowych (0x81 - 0x9F, wartość 0xE0 - 0xFC)|
|Wszystkie wartości z wyjątkiem 1|Nieprawidłowy bajt jednobajtowych lub potencjalnych klientów|**_MBC_ILLEGAL**<br /><br /> ( -1)|Nieprawidłowy znak (wszystkie wartości z wyjątkiem 0x20 - 0x7E, 0xA1 - 0xDF, 0x81 - 0x9F, wartość 0xE0 - 0xFC|
|1|Nieprawidłowy bajt|**_MBC_TRAIL** (2)|Końcowe bajtów znaków wielobajtowych (0x40 - 0x7E, 0x80 - 0xFC)|
|1|Nieprawidłowy bajt|**_MBC_ILLEGAL**<br /><br /> ( -1)|Nieprawidłowy znak (wszystkie wartości z wyjątkiem 0x20 - 0x7E, 0xA1 - 0xDF, 0x81 - 0x9F, wartość 0xE0 - 0xFC|

## <a name="remarks"></a>Uwagi

**_Mbbtype —** funkcja określa typ bajtów w znaków wielobajtowych. Jeśli wartość *typu* oznacza dowolną wartość z wyjątkiem 1, **_mbbtype —** testy nieprawidłowy bajt jednobajtowych lub prowadzić znaków wielobajtowych. Jeśli wartość *typu* 1, **_mbbtype —** testów dla nieprawidłowy bajt znaków wielobajtowych.

Wartość wyjściowa jest zagrożony ustawienie **lc_ctype —** ustawienie kategorii ustawień regionalnych; zobacz [setlocale, _wsetlocale —](setlocale-wsetlocale.md) Aby uzyskać więcej informacji. **_Mbbtype —** wersja tej funkcji używa bieżące ustawienia regionalne tego zachowania zależnych od ustawień regionalnych; **_mbbtype_l —** wersji jest identyczny z tą różnicą, że wykorzystuje ona parametr ustawień regionalnych, który jest przekazywany w zamian . Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

We wcześniejszych wersjach **_mbbtype —** miał nazwę **chkctype**. Nowy kod można użyć **_mbbtype —** zamiast tego.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|---------------------|
|**_mbbtype**|\<mbstring.h>|\<mbctype.h>*|
|**_mbbtype_l**|\<mbstring.h>|\<mbctype.h>*|

\* Definicje manifestu stałe, które są używane jako wartości zwracanych.

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Klasyfikacja bajtów](../../c-runtime-library/byte-classification.md)<br/>
