---
title: "ToAscii, __toascii — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: __toascii
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
dev_langs: C++
helpviewer_keywords:
- toascii function
- string conversion, to ASCII characters
- __toascii function
- ASCII characters, converting to
ms.assetid: a07c0608-b0e2-4da2-a20c-7b64d6a9b77c
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e8b30b01627f412602805b0ef2648cd7d863ad86
ms.sourcegitcommit: ce115fcfb20b4fbc198f0f7b6d0ca3e94d7ce947
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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

*c*  
Znak do konwersji.

## <a name="return-value"></a>Wartość zwracana

`__toascii`Konwertuje wartość *c* ASCII 7-bitowego zakres i zwraca wynik. Brak wartości zwracanej jest zastrzeżony wystąpił błąd.

## <a name="remarks"></a>Uwagi

`__toascii` Procedury konwertuje dany znak znaków ASCII przez obcinanie do mniej znaczącego 7 bitów. Nie inne transformacja jest stosowana.

`__toascii` Procedura jest zdefiniowany jako makra, jeśli _CTYPE_DISABLE_MACROS makro preprocesora nie jest zdefiniowany. W celu zapewnienia zgodności z poprzednimi wersjami `toascii` jest zdefiniowany jako makra tylko wtedy, gdy [&#95; &#95; STDC &#95; &#95; ](../../preprocessor/predefined-macros.md) nie został zdefiniowany lub jest zdefiniowany jako 0; w przeciwnym razie jest niezdefiniowany.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|`toascii`, `__toascii`|C: \<ctype.h ><br /><br /> C++: \<cctype — > lub \<ctype.h >|

`toascii` Makro to rozszerzenie POSIX i `__toascii` jest implementacją rozszerzenia POSIX specyficzne dla firmy Microsoft. Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.

## <a name="see-also"></a>Zobacz też

[Konwersja danych](../../c-runtime-library/data-conversion.md)   
[jest isw — procedury](../../c-runtime-library/is-isw-routines.md)   
[do funkcji](../../c-runtime-library/to-functions.md)