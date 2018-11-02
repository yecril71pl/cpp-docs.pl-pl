---
title: ToAscii, __toascii —
ms.date: 11/04/2016
apiname:
- __toascii
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- __toascii
- toascii
- ctype/toascii
- ctype/__toascii
helpviewer_keywords:
- toascii function
- string conversion, to ASCII characters
- __toascii function
- ASCII characters, converting to
ms.assetid: a07c0608-b0e2-4da2-a20c-7b64d6a9b77c
ms.openlocfilehash: 22f76bdbdb21eb5b3cc9a226c111e321ee2fd0ce
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50578974"
---
# <a name="toascii-toascii"></a>ToAscii, __toascii —

Konwertuje znaki ASCII 7-bitowego przez obcięcie.

## <a name="syntax"></a>Składnia

```C
int __toascii(
   int c
);
#define toascii __toascii
```

### <a name="parameters"></a>Parametry

*c*<br/>
Znak do przekształcenia.

## <a name="return-value"></a>Wartość zwracana

**__toascii —** konwertuje wartość *c* ASCII 7-bitowego zakres i zwraca wynik. Nie zwraca wartości jest rezerwowana w celu wskazania błędu.

## <a name="remarks"></a>Uwagi

**__Toascii —** procedury konwertuje dany znak znak ASCII tworzy go do mniej znaczące bity 7. Nie inne transformacja jest stosowana.

**__Toascii —** procedura jest zdefiniowany jako makro, chyba że _CTYPE_DISABLE_MACROS makro preprocesora jest zdefiniowana. W celu zapewnienia zgodności z poprzednimi wersjami **toascii** jest zdefiniowany jako makro tylko wtedy, gdy [ &#95; &#95;STDC&#95; &#95; ](../../preprocessor/predefined-macros.md) nie został zdefiniowany lub jest zdefiniowana jako 0; w przeciwnym razie jest niezdefiniowany.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**ToAscii**, **__toascii —**|C: \<ctype.h ><br /><br /> C++: \<cctype — > lub \<ctype.h >|

**Toascii** — makro jest rozszerzeniem POSIX i **__toascii —** jest implementacją specyficzne dla Microsoft rozszerzenia POSIX. Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[is, isw, procedury](../../c-runtime-library/is-isw-routines.md)<br/>
[to, funkcje](../../c-runtime-library/to-functions.md)<br/>
