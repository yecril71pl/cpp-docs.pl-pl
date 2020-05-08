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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: dca59f2d31cc5ad843a48e9825ef6a617d46ae4a
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919585"
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

*s*<br/>
Znak do przetestowania.

*Wprowadź*<br/>
Typ bajtu do przetestowania.

*locale*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

**_mbbtype** zwraca typ Byte w ciągu. Ta decyzja jest zależna od kontekstu, określona przez wartość *typu*, która zapewnia warunek testu sterowania. *Typ* jest typem poprzedniego bajtu w ciągu. Stałe manifestu w poniższej tabeli są zdefiniowane w Mbctype. h.

|Wartość *typu*|testy **_mbbtype** dla|Wartość zwracana|*s*|
|---------------------|--------------------------|------------------|---------|
|Dowolna wartość z wyjątkiem 1|Prawidłowy pojedynczy bajt lub bajt wiodący|**_MBC_SINGLE** (0)|Pojedynczy bajt (0x20-0x7E, 0xA1-0xDF)|
|Dowolna wartość z wyjątkiem 1|Prawidłowy pojedynczy bajt lub bajt wiodący|**_MBC_LEAD** (1)|Bajt wiodący znaku wielobajtowego (0x81-0x9F, wartość 0xE0-0xFC)|
|Dowolna wartość z wyjątkiem 1|Prawidłowy bajt jednobajtowy lub wiodący|**_MBC_ILLEGAL**<br /><br /> (-1)|Nieprawidłowy znak (dowolna wartość z wyjątkiem 0x20-0x7E, 0xA1-0xDF, 0x81-0x9F, wartość 0xE0-0xFC|
|1|Prawidłowy bajt końcowy|**_MBC_TRAIL** (2)|Bajt końcowy znaku wielobajtowego (0x40-0x7E, 0x80-0xFC)|
|1|Prawidłowy bajt końcowy|**_MBC_ILLEGAL**<br /><br /> (-1)|Nieprawidłowy znak (dowolna wartość z wyjątkiem 0x20-0x7E, 0xA1-0xDF, 0x81-0x9F, wartość 0xE0-0xFC|

## <a name="remarks"></a>Uwagi

Funkcja **_mbbtype** określa typ bajtu w znaku wielobajtowym. Jeśli wartość *typu* jest dowolnej wartości z wyjątkiem 1, **_mbbtype** testy dla prawidłowego bajtu jednobajtowego lub potencjalnego klienta znaku wielobajtowego. Jeśli wartość *typu* wynosi 1, **_mbbtype** testy dla prawidłowego bajtu końcowego znaku wielobajtowego.

Wartość wyjściowa jest zależna od ustawienia ustawienia kategorii **LC_CTYPE** ustawień regionalnych; Aby uzyskać więcej informacji [, zobacz setlocals, _wsetlocale](setlocale-wsetlocale.md) . Wersja **_mbbtype** tej funkcji używa bieżących ustawień regionalnych dla tego zachowania zależnego od ustawień regionalnych; wersja **_mbbtype_l** jest identyczna z tą różnicą, że używa zamiast tego parametru ustawień regionalnych, który został przekazaną. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

We wcześniejszych wersjach **_mbbtype** miał nazwę **chkctype**. W przypadku nowego kodu Użyj zamiast tego **_mbbtype** .

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalny nagłówek|
|-------------|---------------------|---------------------|
|**_mbbtype**|\<mbstring. h>|\<Mbctype. h> *|
|**_mbbtype_l**|\<mbstring. h>|\<Mbctype. h> *|

\*Dla definicji stałych manifestu, które są używane jako wartości zwracane.

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Klasyfikacja bajtów](../../c-runtime-library/byte-classification.md)<br/>
