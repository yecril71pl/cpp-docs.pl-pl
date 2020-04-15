---
title: _ismbbkprint, _ismbbkprint_l
ms.date: 4/2/2020
api_name:
- _ismbbkprint
- _ismbbkprint_l
- _o__ismbbkprint
- _o__ismbbkprint_l
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
- _ismbbkprint_l
- ismbbkprint
- _ismbbkprint
- ismbbkprint_l
helpviewer_keywords:
- _ismbbkprint function
- ismbbkprint_l function
- ismbbkprint function
- _ismbbkprint_l function
ms.assetid: 8d1d3258-1e34-4365-81ed-97c95de25475
ms.openlocfilehash: e59d06678b2601375bf3174fa84bc261c350c4dd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81343630"
---
# <a name="_ismbbkprint-_ismbbkprint_l"></a>_ismbbkprint, _ismbbkprint_l

Określa, czy określony znak wielobajtowy jest symbolem interpunkcyjnym.

## <a name="syntax"></a>Składnia

```C
int _ismbbkprint(
   unsigned int c
);
int _ismbbkprint_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*C*<br/>
Całkowita ć, która ma zostać przetestowana.

*Ustawień regionalnych*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

**_ismbbkprint** zwraca wartość niezerową, jeśli liczba całkowita *c* jest tekstem nienawiązanym ascii lub symbolem interpunkcyjnym innego niż ASCII lub 0, jeśli nie jest. Na przykład tylko na stronie kodowej 932 **_ismbbkprint** testy znaków interpunkcyjnych katakana alfanumeryczne lub katakana (zakres: 0xA1 - 0xDF). **_ismbbkprint** używa bieżących ustawień ustawień znaków zależnych od ustawień ustawień ustawień regionalnych. **_ismbbkprint_l** jest identyczna, z tą różnicą, że używa ustawień regionalnych przekazanych. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

## <a name="remarks"></a>Uwagi

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_ismbbkprint**|\<mbctype.h>|
|**_ismbbkprint_l**|\<mbctype.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Klasyfikacja bajtów](../../c-runtime-library/byte-classification.md)<br/>
[_ismbb, procedury](../../c-runtime-library/ismbb-routines.md)<br/>
