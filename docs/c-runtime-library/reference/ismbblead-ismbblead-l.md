---
title: _ismbblead, _ismbblead_l
ms.date: 11/04/2016
apiname:
- _ismbblead_l
- _ismbblead
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
ms.openlocfilehash: 7bf8e8c88153e2f22cfa08bb35ff8d4ba01a8804
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157214"
---
# <a name="ismbblead-ismbbleadl"></a>_ismbblead, _ismbblead_l

Testuje znak, aby ustalić, czy jest ono bajt znaku wielobajtowego.

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

*c*<br/>
Liczba całkowita do zbadania.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość różną od zera, jeśli liczba całkowita *c* jest pierwszym bajtem znaku wielobajtowego.

## <a name="remarks"></a>Uwagi

Znaki wielobajtowe składają się z bajtu wiodącego, po którym następuje bajt. Bajty wiodące są odróżniane przez występowanie w określonym zakresie dla danego zestawu znaków. Na przykład w kodzie strony 932 tylko, bajty wiodące dostosować w zakresie 0x81-0x9F i 0xE0 — 0xFC.

**_ismbblead** używa bieżących ustawień regionalnych dla zachowań zależnych od ustawień regionalnych. **_ismbblead_l —** jest identyczna, z tą różnicą, że używa ustawień regionalnych przekazanych w zamian. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_istlead**|Zawsze zwraca wartość false|**_ismbblead**|Zawsze zwraca wartość false|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|---------------------|
|**_ismbblead**|\<mbctype.h > lub \<mbstring.h >|\<ctype.h>,* \<limits.h>, \<stdlib.h>|
|**_ismbblead_l**|\<mbctype.h > lub \<mbstring.h >|\<ctype.h>,* \<limits.h>, \<stdlib.h>|

\* Dla stałych manifestu do warunków badania.

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Klasyfikacja bajtów](../../c-runtime-library/byte-classification.md)<br/>
[_ismbb, procedury](../../c-runtime-library/ismbb-routines.md)<br/>
