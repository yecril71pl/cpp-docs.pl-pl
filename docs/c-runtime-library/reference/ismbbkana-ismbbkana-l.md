---
title: _ismbbkana, _ismbbkana_l
ms.date: 4/2/2020
api_name:
- _ismbbkana_l
- _ismbbkana
- _o__ismbbkana
- _o__ismbbkana_l
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
- _ismbbkana_l
- ismbbkana_l
- ismbbkana
- _ismbbkana
helpviewer_keywords:
- _ismbbkana_l function
- _ismbbkana function
- ismbbkana function
- ismbbkana_l function
ms.assetid: 64d4eb4a-205a-40ef-be35-ff9d77fabbaf
ms.openlocfilehash: 288c23ac11104ed994719fae8576cdc3597d7478
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81343639"
---
# <a name="_ismbbkana-_ismbbkana_l"></a>_ismbbkana, _ismbbkana_l

Testy dla symbolu katakana i jest specyficzne dla strony kodowej 932.

## <a name="syntax"></a>Składnia

```C
int _ismbbkana(
   unsigned int c
);
int _ismbbkana_l(
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

**_ismbbkana** zwraca wartość niezerową, jeśli liczba całkowita *c* jest symbolem katakana lub 0, jeśli nie jest. **_ismbbkana** używa bieżących ustawień regionalnych dla informacji o znakach zależnych od ustawień regionalnych. **_ismbbkana_l** jest identyczna, z tą różnicą, że używa obiektu ustawień regionalnych przekazanych. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

## <a name="remarks"></a>Uwagi

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_ismbbkana**|\<mbctype.h>|
|**_ismbbkana_l**|\<mbctype.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Klasyfikacja bajtów](../../c-runtime-library/byte-classification.md)<br/>
[_ismbb, procedury](../../c-runtime-library/ismbb-routines.md)<br/>
