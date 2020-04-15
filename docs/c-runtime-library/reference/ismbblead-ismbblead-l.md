---
title: _ismbblead, _ismbblead_l
description: W tym artykule opisano _ismbblead i _ismbblead_l funkcji biblioteki wykonawczej języka Microsoft C (CRT).
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: ee3085d49a27f2f3c97c6578463cf3a0598b73c7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81343575"
---
# <a name="_ismbblead-_ismbblead_l"></a>_ismbblead, _ismbblead_l

Testuje znak, aby ustalić, czy jest to bajt wiodący znaku wielobajtowego.

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

*C*\
Całkowita ć, która ma zostać przetestowana.

*Ustawień regionalnych*\
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość niezerową, jeśli liczba całkowita *c* jest pierwszym bajtem znaku wielobajtowego.

## <a name="remarks"></a>Uwagi

Znaki wielobajtowe składają się z byte potencjalnego klienta, po którym następuje bajt końcowy. Bajty potencjalnych są wyróżniane przez bycie w określonym zakresie dla danego zestawu znaków. Na przykład tylko na stronie kodowej 932 bajty potencjalnych potencjalnych potencjalnych potencjalnych potencjalnych klienty mają zasięg od 0x81 - 0x9F i 0xE0 - 0xFC.

**_ismbblead** używa bieżących ustawień regionalnych dla zachowania zależnego od ustawień regionalnych. **_ismbblead_l** jest identyczna, z tą różnicą, że używa ustawień regionalnych przekazanych zamiast. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

Gdy ustawienia regionalne to UTF-8, **_ismbblead** i **_ismbblead_l** zawsze zwracać 0 (false), niezależnie od *tego,* czy c jest bajtem wiodącym, czy nie.

**_ismbblead** i **_ismbblead_l** są specyficzne dla firmy Microsoft, a nie są częścią biblioteki Standard C. Nie zalecamy używania ich tam, gdzie chcesz przenośny kod. W przypadku zgodności ze standardem C należy użyć **mbrlen.**

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania rutynowych tekstu ogólnego

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_istlead**|Zawsze zwraca fałsz|**_ismbblead**|Zawsze zwraca fałsz|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalny nagłówek|
|-------------|---------------------|---------------------|
|**_ismbblead**|\<mbctype.h> lub \<mbstring.h>|\<ctype.h>,* \<limits.h>, \<stdlib.h>|
|**_ismbblead_l**|\<mbctype.h> lub \<mbstring.h>|\<ctype.h>,* \<limits.h>, \<stdlib.h>|

\*Dla stałych manifestu dla warunków badania.

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Klasyfikacja bajtów](../../c-runtime-library/byte-classification.md)\
[procedury _ismbb](../../c-runtime-library/ismbb-routines.md)\
[mbrlen](mbrlen.md)
