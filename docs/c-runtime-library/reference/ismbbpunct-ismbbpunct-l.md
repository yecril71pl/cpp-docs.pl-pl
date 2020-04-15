---
title: _ismbbpunct, _ismbbpunct_l
ms.date: 4/2/2020
api_name:
- _ismbbpunct
- _ismbbpunct_l
- _o__ismbbpunct
- _o__ismbbpunct_l
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
- ismbbpunct
- ismbbpunct_l
- _ismbbpunct_l
- _ismbbpunct
helpviewer_keywords:
- ismbbpunct function
- _ismbbpunct function
- ismbbpunct_l function
- _ismbbpunct_l function
ms.assetid: 1976c9d3-7d1a-415f-ac52-2715c7bb56eb
ms.openlocfilehash: db0725215b6568300602c55ca253d959c27aedc1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81343460"
---
# <a name="_ismbbpunct-_ismbbpunct_l"></a>_ismbbpunct, _ismbbpunct_l

Określa, czy określony znak jest znakiem interpunkcyjnym.

## <a name="syntax"></a>Składnia

```C
int _ismbbpunct(
   unsigned int c
);
int _ismbbpunct_l(
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

**_ismbbpunct** zwraca wartość niezerową, jeśli liczba całkowita *c* jest symbolem interpunkcyjnym nienawiązanym do ASCII. **_ismbbpunct** używa bieżących ustawień regionalnych dla wszystkich ustawień znaków zależnych od ustawień regionalnych. **_ismbbpunct_l** jest identyczna, z tą różnicą, że używa ustawień regionalnych, które są przekazywane. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

## <a name="remarks"></a>Uwagi

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_ismbbpunct**|\<mbctype.h>|
|**_ismbbpunct_l**|\<mbctype.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Klasyfikacja bajtów](../../c-runtime-library/byte-classification.md)<br/>
[_ismbb, procedury](../../c-runtime-library/ismbb-routines.md)<br/>
