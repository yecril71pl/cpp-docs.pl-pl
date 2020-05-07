---
title: _ismbblead, _ismbblead_l
description: Opisuje funkcje _ismbblead i _ismbblead_l biblioteki środowiska uruchomieniowego Microsoft C (CRT).
ms.date: 4/2/2020
api_name:
- _ismbblead_l
- _ismbblead
- _o__ismbblead
- _o__ismbblead_l
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
- ismbblead_l
- istlead
- _ismbblead
- _ismbblead_l
- ismbblead
- _istlead
helpviewer_keywords:
- _ismbblead_l function
- ismbblead function
- _ismbblead function
- istlead function
- ismbblead_l function
- _istlead function
ms.assetid: 2abc6f75-ed5c-472e-bfd0-e905a1835ccf
ms.openlocfilehash: 7680793b71c4535ed75433ac98167e52a39896ba
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82918667"
---
# <a name="_ismbblead-_ismbblead_l"></a>_ismbblead, _ismbblead_l

Testuje znak, aby określić, czy jest to bajt wiodący znaku wielobajtowego.

## <a name="syntax"></a>Składnia

```C
int _ismbblead(
   unsigned int c
);
int _ismbblead_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*s*\
Liczba całkowita do przetestowania.

*ustawienie*\
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość różną od zera, jeśli liczba całkowita *c* jest pierwszym bajtem znaku wielobajtowego.

## <a name="remarks"></a>Uwagi

Znaki wielobajtowe składają się z bajtu wiodącego, po którym następuje bajt końcowy. Bajty potencjalnych klientów są rozróżniane w określonym zakresie dla danego zestawu znaków. Na przykład, tylko na stronie kodowej 932, zakresem potencjalnych bajtów od 0x81-0x9F i wartość 0xE0-0xFC.

**_ismbblead** używa bieżących ustawień regionalnych dla zachowań zależnych od ustawień regionalnych. **_ismbblead_l** jest identyczny, z tą różnicą, że w zamian korzysta z przekazaną ustawieniami regionalnymi. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

Jeśli ustawienia regionalne to UTF-8, **_ismbblead** i **_ismbblead_l** zawsze zwracają wartość 0 (false), niezależnie od tego, czy *c* jest bajtem wiodącym, czy nie.

**_ismbblead** i **_ismbblead_l** są charakterystyczne dla firmy Microsoft, a nie częścią standardowej biblioteki C. Nie zalecamy korzystania z nich w przypadku, gdy potrzebny jest kod przenośny. W przypadku standardowej zgodności C zamiast tego należy użyć **mbrlen** .

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedury tekstu ogólnego

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_istlead**|Zawsze zwraca wartość false|**_ismbblead**|Zawsze zwraca wartość false|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalny nagłówek|
|-------------|---------------------|---------------------|
|**_ismbblead**|\<Mbctype. h> lub \<mbstring. h>|\<CType. h>, * \<Limits. h> \<, STDLIB. h>|
|**_ismbblead_l**|\<Mbctype. h> lub \<mbstring. h>|\<CType. h>, * \<Limits. h> \<, STDLIB. h>|

\*Dla stałych manifestu dla warunków testowych.

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Klasyfikacja bajtów](../../c-runtime-library/byte-classification.md)\
[procedury _ismbb](../../c-runtime-library/ismbb-routines.md)\
[mbrlen](mbrlen.md)
