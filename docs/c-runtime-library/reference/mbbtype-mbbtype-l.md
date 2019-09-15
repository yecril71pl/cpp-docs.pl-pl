---
title: _mbbtype, _mbbtype_l
ms.date: 11/04/2016
api_name:
- _mbbtype
- _mbbtype_l
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
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: ba4311921a0924d3f447feb1929a81ae1d816604
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952719"
---
# <a name="_mbbtype-_mbbtype_l"></a>_mbbtype, _mbbtype_l

Zwraca typ Byte na podstawie poprzedniego bajtu.

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Znak do przetestowania.

*type*<br/>
Typ bajtu do przetestowania.

*ustawienie*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

**_mbbtype** zwraca typ Byte w ciągu. Ta decyzja jest zależna od kontekstu, określona przez wartość *typu*, która zapewnia warunek testu sterowania. *Typ* jest typem poprzedniego bajtu w ciągu. Stałe manifestu w poniższej tabeli są zdefiniowane w Mbctype. h.

|Wartość *typu*|**_mbbtype** testy dla|Wartość zwracana|*c*|
|---------------------|--------------------------|------------------|---------|
|Dowolna wartość z wyjątkiem 1|Prawidłowy pojedynczy bajt lub bajt wiodący|**_MBC_SINGLE** 2,0|Pojedynczy bajt (0x20-0x7E, 0xA1-0xDF)|
|Dowolna wartość z wyjątkiem 1|Prawidłowy pojedynczy bajt lub bajt wiodący|**_MBC_LEAD** JEDNO|Bajt wiodący znaku wielobajtowego (0x81-0x9F, wartość 0xE0-0xFC)|
|Dowolna wartość z wyjątkiem 1|Prawidłowy bajt jednobajtowy lub wiodący|**_MBC_ILLEGAL**<br /><br /> ( -1)|Nieprawidłowy znak (dowolna wartość z wyjątkiem 0x20-0x7E, 0xA1-0xDF, 0x81-0x9F, wartość 0xE0-0xFC|
|1|Prawidłowy bajt końcowy|**_MBC_TRAIL** DWÓCH|Bajt końcowy znaku wielobajtowego (0x40-0x7E, 0x80-0xFC)|
|1|Prawidłowy bajt końcowy|**_MBC_ILLEGAL**<br /><br /> ( -1)|Nieprawidłowy znak (dowolna wartość z wyjątkiem 0x20-0x7E, 0xA1-0xDF, 0x81-0x9F, wartość 0xE0-0xFC|

## <a name="remarks"></a>Uwagi

Funkcja **_mbbtype** określa typ bajtu w znaku wielobajtowym. Jeśli wartość *typu* jest dowolnej wartości z wyjątkiem 1, **_mbbtype** testów dla prawidłowego bajtu jednobajtowego lub potencjalnego klienta znaku wielobajtowego. Jeśli wartość *typu* to 1, **_mbbtype** testuje prawidłowy bajt końcowy znaku wielobajtowego.

Wartość wyjściowa jest zależna od ustawienia **LC_CTYPE** kategorii ustawień regionalnych; Zobacz [setlocaling, _wsetlocale,](setlocale-wsetlocale.md) Aby uzyskać więcej informacji. Wersja **_mbbtype** tej funkcji używa bieżących ustawień regionalnych dla tego zachowania zależnego od ustawień regionalnych; wersja **_mbbtype_l** jest identyczna z tą różnicą, że używa zamiast tego parametru ustawień regionalnych, który został przekazaną. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

We wcześniejszych wersjach **_mbbtype** miał nazwę **chkctype**. W przypadku nowego kodu zamiast tego należy użyć **_mbbtype** .

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalny nagłówek|
|-------------|---------------------|---------------------|
|**_mbbtype**|\<mbstring.h>|\<mbctype.h>*|
|**_mbbtype_l**|\<mbstring.h>|\<mbctype.h>*|

\*Dla definicji stałych manifestu, które są używane jako wartości zwracane.

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Klasyfikacja bajtów](../../c-runtime-library/byte-classification.md)<br/>
