---
title: ToAscii, __toascii — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- toascii function
- string conversion, to ASCII characters
- __toascii function
- ASCII characters, converting to
ms.assetid: a07c0608-b0e2-4da2-a20c-7b64d6a9b77c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cead516a7e298e56d13d8f1a09a054057796ca64
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
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
Znak do konwersji.

## <a name="return-value"></a>Wartość zwracana

**__toascii —** konwertuje wartość *c* ASCII 7-bitowego zakres i zwraca wynik. Brak wartości zwracanej jest zastrzeżony wystąpił błąd.

## <a name="remarks"></a>Uwagi

**__Toascii —** procedury konwertuje dany znak znaków ASCII przez obcinanie do mniej znaczącego 7 bitów. Nie inne transformacja jest stosowana.

**__Toascii —** procedura jest zdefiniowany jako makra, jeśli _CTYPE_DISABLE_MACROS makro preprocesora nie jest zdefiniowany. W celu zapewnienia zgodności z poprzednimi wersjami **toascii** jest zdefiniowany jako makra tylko wtedy, gdy [ &#95; &#95;STDC&#95; &#95; ](../../preprocessor/predefined-macros.md) nie został zdefiniowany lub jest zdefiniowany jako 0; w przeciwnym razie jest niezdefiniowany.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**ToAscii**, **__toascii —**|C: \<ctype.h ><br /><br /> C++: \<cctype — > lub \<ctype.h >|

**Toascii** makro to rozszerzenie POSIX i **__toascii —** jest implementacją rozszerzenia POSIX specyficzne dla firmy Microsoft. Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[is, isw, procedury](../../c-runtime-library/is-isw-routines.md)<br/>
[to, funkcje](../../c-runtime-library/to-functions.md)<br/>
