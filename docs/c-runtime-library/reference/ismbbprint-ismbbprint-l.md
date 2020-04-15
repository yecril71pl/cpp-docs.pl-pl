---
title: _ismbbprint, _ismbbprint_l
ms.date: 4/2/2020
api_name:
- _ismbbprint_l
- _ismbbprint
- _o__ismbbprint
- _o__ismbbprint_l
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
- _ismbbprint_l
- _ismbbprint
- ismbbprint
- ismbbprint_l
helpviewer_keywords:
- ismbbprint_l function
- ismbbprint function
- _ismbbprint function
- _ismbbprint_l function
ms.assetid: d08a061c-18a8-48f2-a75d-bff4870aec9d
ms.openlocfilehash: 8da69247d090c2067b0efda3c47f92bbeb729e49
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81343525"
---
# <a name="_ismbbprint-_ismbbprint_l"></a>_ismbbprint, _ismbbprint_l

Określa, czy określony znak wielobajtowy jest znakiem wydruku.

## <a name="syntax"></a>Składnia

```C
int _ismbbprint(
   unsigned int c
);
int _ismbbprint_l(
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

**_ismbbprint** zwraca wartość niezerową, jeśli wyrażenie:

`isprint(c) || _ismbbkprint(c)`

jest niezerowy dla *c*lub 0, jeśli nie jest. **_ismbbprint** używa bieżących ustawień regionalnych dla zachowania zależnego od ustawień regionalnych. **_ismbbprint_l** jest identyczna, z tą różnicą, że używa ustawień regionalnych przekazanych zamiast. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

## <a name="remarks"></a>Uwagi

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_ismbbprint**|\<mbctype.h>|
|**_ismbbprint_l**|\<mbctype.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Klasyfikacja bajtów](../../c-runtime-library/byte-classification.md)<br/>
[_ismbb, procedury](../../c-runtime-library/ismbb-routines.md)<br/>
