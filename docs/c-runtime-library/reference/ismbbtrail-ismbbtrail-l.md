---
title: _ismbbtrail, _ismbbtrail_l
ms.date: 11/04/2016
apiname:
- _ismbbtrail
- _ismbbtrail_l
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
ms.openlocfilehash: 5c09884f013e878fca516388f1ad933a2a08b35a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62286865"
---
# <a name="ismbbtrail-ismbbtraill"></a>_ismbbtrail, _ismbbtrail_l

Określa, czy bajt jest bajt znaku wielobajtowego.

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
Liczba całkowita do zbadania.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

**_ismbbtrail** zwraca wartość różną od zera, jeśli liczba całkowita *c* jest drugi bajt znaku wielobajtowego. Na przykład w kodzie strony 932 tylko, prawidłowe zakresy są 0x40 — 0x7E oraz 0x80 — 0xFC.

## <a name="remarks"></a>Uwagi

**_ismbbtrail** używa bieżących ustawień regionalnych dla zachowań zależnych od ustawień regionalnych. **_ismbbtrail_l —** jest identyczna, z tą różnicą, że używa ustawień regionalnych przekazanych w zamian. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|---------------------|
|**_ismbbtrail**|\<mbctype.h > lub \<mbstring.h >|\<ctype.h>,* \<limits.h>, \<stdlib.h>|
|**_ismbbtrail_l**|\<mbctype.h > lub \<mbstring.h >|\<ctype.h>,* \<limits.h>, \<stdlib.h>|

\* Dla stałych manifestu do warunków badania.

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Klasyfikacja bajtów](../../c-runtime-library/byte-classification.md)<br/>
[_ismbb, procedury](../../c-runtime-library/ismbb-routines.md)<br/>
