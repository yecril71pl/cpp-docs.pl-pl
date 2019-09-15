---
title: toascii, __toascii
ms.date: 11/04/2016
api_name:
- __toascii
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
- api-ms-win-crt-convert-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 09df829511b38b87cb41e32a59bee9f38a9b8f32
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957473"
---
# <a name="toascii-__toascii"></a>toascii, __toascii

Konwertuje znaki na 7-bitowe ASCII przez obcinanie.

## <a name="syntax"></a>Składnia

```C
int __toascii(
   int c
);
#define toascii __toascii
```

### <a name="parameters"></a>Parametry

*c*<br/>
Znak do przekonwertowania.

## <a name="return-value"></a>Wartość zwracana

**__toascii** konwertuje wartość *c* na 7-bitowy zakres ASCII i zwraca wynik. Brak wartości zwracanej zastrzeżonej do wskazania błędu.

## <a name="remarks"></a>Uwagi

Procedura **__toascii** konwertuje dany znak na znak ASCII poprzez obcinanie go do 7 bitów o niskiej kolejności. Nie są stosowane żadne inne przekształcenia.

Procedura **__toascii** jest definiowana jako makro, chyba że zdefiniowane zostanie makro preprocesora _CTYPE_DISABLE_MACROS. W celu zapewnienia zgodności z poprzednimi wersjami **ToAscii** jest definiowana jako makro tylko wtedy, gdy [ &#95; &#95;STDC&#95; ](../../preprocessor/predefined-macros.md) nie jest zdefiniowany lub jest zdefiniowany jako 0; w przeciwnym razie jest to niezdefiniowane.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**ToAscii**, **__toascii**|C: \<CType. h ><br /><br /> C++: \<cctype > lub \<CType. h >|

Makro **ToAscii** jest rozszerzeniem POSIX, a **__toascii** jest implementacją systemu POSIX przez firmę Microsoft. Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Konwersja danych](../../c-runtime-library/data-conversion.md)<br/>
[is, isw, procedury](../../c-runtime-library/is-isw-routines.md)<br/>
[to, funkcje](../../c-runtime-library/to-functions.md)<br/>
