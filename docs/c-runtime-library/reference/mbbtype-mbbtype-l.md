---
title: _mbbtype, _mbbtype_l
ms.date: 4/2/2020
api_name:
- _mbbtype
- _mbbtype_l
- _o__mbbtype
- _o__mbbtype_l
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
ms.openlocfilehash: 7e2e818ed70ec393e4f81008f76ca9efe9cfa7e7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341408"
---
# <a name="_mbbtype-_mbbtype_l"></a>_mbbtype, _mbbtype_l

Zwraca typ bajtów na podstawie poprzedniego bajtu.

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobjęte w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*C*<br/>
Znak do przetestowania.

*Typu*<br/>
Typ bajtu do przetestowania.

*Ustawień regionalnych*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

**_mbbtype** zwraca typ bajtu w ciągu. Ta decyzja jest kontekstowa, określona przez wartość *typu*, która zapewnia warunek testu kontrolnego. *jest* typem poprzedniego bajtu w ciągu. Stałe manifestu w poniższej tabeli są zdefiniowane w Mbctype.h.

|Wartość *typu*|**_mbbtype** testy|Wartość zwracana|*C*|
|---------------------|--------------------------|------------------|---------|
|Dowolna wartość z wyjątkiem 1|Prawidłowy pojedynczy bajt lub bajt potencjalnego klienta|**_MBC_SINGLE** (0)|Pojedynczy bajt (0x20 - 0x7E, 0xA1 - 0xDF)|
|Dowolna wartość z wyjątkiem 1|Prawidłowy pojedynczy bajt lub bajt potencjalnego klienta|**_MBC_LEAD** (1)|Bajt wiodący znaku wielobajtowego (0x81 - 0x9F, 0xE0 - 0xFC)|
|Dowolna wartość z wyjątkiem 1|Prawidłowy bajt jedno bajtowy lub wiodący|**_MBC_ILLEGAL**<br /><br /> ( -1)|Nieprawidłowy znak (dowolna wartość z wyjątkiem 0x20 - 0x7E, 0xA1 - 0xDF, 0x81 - 0x9F, 0xE0 - 0xFC|
|1|Prawidłowy bajt szlaku|**_MBC_TRAIL** (2)|Bajt spływowy znaku wielobajtowego (0x40 - 0x7E, 0x80 - 0xFC)|
|1|Prawidłowy bajt szlaku|**_MBC_ILLEGAL**<br /><br /> ( -1)|Nieprawidłowy znak (dowolna wartość z wyjątkiem 0x20 - 0x7E, 0xA1 - 0xDF, 0x81 - 0x9F, 0xE0 - 0xFC|

## <a name="remarks"></a>Uwagi

Funkcja **_mbbtype** określa typ bajtu w znaku wielobajtowym. Jeśli wartość *typu* jest dowolną wartością z wyjątkiem 1, **_mbbtype** testy dla prawidłowego bajtu jednobajtowego lub wiodącego znaku wielobajtowego. Jeśli wartość *typu* wynosi 1, **_mbbtype** testy prawidłowego bajtu szlaku znaku wielobajtowego.

Na wartość wyjściową ma wpływ ustawienie **LC_CTYPE** kategorii ustawień regionalnych; zobacz [setlocale, _wsetlocale aby](setlocale-wsetlocale.md) uzyskać więcej informacji. **Wersja _mbbtype** tej funkcji używa bieżących ustawień regionalnych dla tego zachowania zależnego od ustawień regionalnych; _mbbtype_l **_mbbtype_l** wersja jest identyczna, z tą różnicą, że używa parametru ustawień regionalnych, który jest przekazywany zamiast. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

We wcześniejszych wersjach **_mbbtype** został nazwany **chkctype**. W przypadku nowego kodu należy użyć **_mbbtype.**

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalny nagłówek|
|-------------|---------------------|---------------------|
|**_mbbtype**|\<mbstring.h>|\<mbctype.h>*|
|**_mbbtype_l**|\<mbstring.h>|\<mbctype.h>*|

\*Dla definicji stałych manifestu, które są używane jako wartości zwracane.

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Klasyfikacja bajtów](../../c-runtime-library/byte-classification.md)<br/>
