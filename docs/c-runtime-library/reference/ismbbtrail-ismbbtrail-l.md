---
title: _ismbbtrail, _ismbbtrail_l
ms.date: 4/2/2020
api_name:
- _ismbbtrail
- _ismbbtrail_l
- _o__ismbbtrail
- _o__ismbbtrail_l
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
ms.openlocfilehash: 5e8615adf5d17986c1a52658fe5d680cc326976a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81343397"
---
# <a name="_ismbbtrail-_ismbbtrail_l"></a>_ismbbtrail, _ismbbtrail_l

Określa, czy bajt jest bajtem spływowym znaku wielobajtowego.

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

*C*<br/>
Liczba całkowita do przetestowania.

*Ustawień regionalnych*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

**_ismbbtrail** zwraca wartość niezerową, jeśli liczba całkowita *c* jest drugim bajtem znaku wielobajtowego. Na przykład tylko na stronie kodowej 932 prawidłowe zakresy to od 0x40 do 0x7E i od 0x80 do 0xFC.

## <a name="remarks"></a>Uwagi

**_ismbbtrail** używa bieżących ustawień regionalnych dla zachowania zależnego od ustawień regionalnych. **_ismbbtrail_l** jest identyczna, z tą różnicą, że używa ustawień regionalnych, które są przekazywane zamiast. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalny nagłówek|
|-------------|---------------------|---------------------|
|**_ismbbtrail**|\<mbctype.h> lub \<mbstring.h>|\<ctype.h>,* \<limits.h>, \<stdlib.h>|
|**_ismbbtrail_l**|\<mbctype.h> lub \<mbstring.h>|\<ctype.h>,* \<limits.h>, \<stdlib.h>|

\*Dla stałych manifestu dla warunków badania.

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Klasyfikacja bajtów](../../c-runtime-library/byte-classification.md)<br/>
[_ismbb, procedury](../../c-runtime-library/ismbb-routines.md)<br/>
