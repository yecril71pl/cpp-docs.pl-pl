---
title: _ismbbprint —, _ismbbprint_l — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _ismbbprint_l
- _ismbbprint
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
- _ismbbprint_l
- _ismbbprint
- ismbbprint
- ismbbprint_l
dev_langs:
- C++
helpviewer_keywords:
- ismbbprint_l function
- ismbbprint function
- _ismbbprint function
- _ismbbprint_l function
ms.assetid: d08a061c-18a8-48f2-a75d-bff4870aec9d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 49618a119f089e70e88bbdb9efcdae9bab616560
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32400079"
---
# <a name="ismbbprint-ismbbprintl"></a>_ismbbprint, _ismbbprint_l

Określa, czy określony znaków wielobajtowych jest znak wydruku.

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

*c*<br/>
Liczba całkowita ma zostać przetestowana.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

**_ismbbprint —** zwraca wartość niezerową, jeśli wyrażenie:

`isprint(c) || _ismbbkprint(c)`

jest różna od zera dla *c*, lub wartość 0, jeśli nie jest. **_ismbbprint —** używa bieżące ustawienia regionalne dla dowolnego zachowanie zależnych od ustawień regionalnych. **_ismbbprint_l —** jest identyczny z tą różnicą, że używa ustawień regionalnych przekazano zamiast tego. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_ismbbprint**|\<mbctype.h>|
|**_ismbbprint_l**|\<mbctype.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Klasyfikacja bajtów](../../c-runtime-library/byte-classification.md)<br/>
[_ismbb, procedury](../../c-runtime-library/ismbb-routines.md)<br/>
