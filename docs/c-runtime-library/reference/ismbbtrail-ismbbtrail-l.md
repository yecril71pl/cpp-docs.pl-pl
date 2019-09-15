---
title: _ismbbtrail, _ismbbtrail_l
ms.date: 11/04/2016
api_name:
- _ismbbtrail
- _ismbbtrail_l
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
- _ismbbtrail
- ismbbtrail
- _ismbbtrail_l
- ismbbtrail_l
helpviewer_keywords:
- ismbbtrail_l function
- _ismbbtrail function
- _ismbbtrail_l function
- ismbbtrail function
ms.assetid: dfdd0292-960b-4c1d-bf11-146e0fc80247
ms.openlocfilehash: e445de41b05ac4829bdf108d1c98113cd5240ec0
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953970"
---
# <a name="_ismbbtrail-_ismbbtrail_l"></a>_ismbbtrail, _ismbbtrail_l

Określa, czy bajt jest bajtem końcowym znaku wielobajtowego.

## <a name="syntax"></a>Składnia

```C
int _ismbbtrail(
   unsigned int c
);
int _ismbbtrail_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*c*<br/>
Liczba całkowita, która ma zostać przetestowana.

*ustawienie*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

**_ismbbtrail** zwraca wartość różną od zera, jeśli liczba całkowita *c* jest drugim bajtem znaku wielobajtowego. Na przykład, na stronie kodowej 932, prawidłowymi zakresami są 0x40 0x7E i 0x80 do 0xFC.

## <a name="remarks"></a>Uwagi

**_ismbbtrail** używa bieżących ustawień regionalnych dla zachowań zależnych od ustawień regionalnych. **_ismbbtrail_l** jest identyczny, z tą różnicą, że używa zamiast tego ustawień regionalnych, które zostały przesłane. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalny nagłówek|
|-------------|---------------------|---------------------|
|**_ismbbtrail**|\<Mbctype. h > lub \<mbstring. h >|\<ctype.h>,* \<limits.h>, \<stdlib.h>|
|**_ismbbtrail_l**|\<Mbctype. h > lub \<mbstring. h >|\<ctype.h>,* \<limits.h>, \<stdlib.h>|

\*Dla stałych manifestu dla warunków testowych.

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Klasyfikacja bajtów](../../c-runtime-library/byte-classification.md)<br/>
[_ismbb, procedury](../../c-runtime-library/ismbb-routines.md)<br/>
