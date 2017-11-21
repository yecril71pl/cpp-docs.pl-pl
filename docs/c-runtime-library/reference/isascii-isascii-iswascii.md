---
title: "isascii —, __isascii —, iswascii — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- iswascii
- __isascii
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- iswascii
- istascii
- __isascii
- _istascii
- isascii
- ctype/isascii
- ctype/__isascii
- corecrt_wctype/iswascii
dev_langs: C++
helpviewer_keywords:
- __isascii function
- _isascii function
- isascii function
- _istascii function
- istascii function
- iswascii function
ms.assetid: ba4325ad-7cb3-4fb9-b096-58906d67971a
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6f321411fca27d22540d4dc63c56774522b04a5e
ms.sourcegitcommit: ca2f94dfd015e0098a6eaf5c793ec532f1c97de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="isascii-isascii-iswascii"></a>isascii —, __isascii —, iswascii —

Określa, czy określonego znaku jest znakiem ASCII.

## <a name="syntax"></a>Składnia

```C
int __isascii(
   int c
);
int iswascii(
   wint_t c
);

#define isascii __isascii
```

### <a name="parameters"></a>Parametry

*c*  
Liczba całkowita do testowania.

## <a name="return-value"></a>Wartość zwracana

Każdy z tych procedur zwraca różną od zera, jeśli `c` jest reprezentację określonego obiektu znaków ASCII. `__isascii`Zwraca wartość niezerową, jeśli `c` jest znakiem ASCII (w zakresie 0x00 - 0x7F). `iswascii`Zwraca wartość niezerową, jeśli `c` odzwierciedla znaków dwubajtowych znaków ASCII. Każdy z tych procedur zwraca 0, jeśli `c` nie spełnia warunku.

## <a name="remarks"></a>Uwagi

Zarówno `__isascii` i `iswascii` są zaimplementowane jako makra, chyba że jest zdefiniowane _CTYPE_DISABLE_MACROS makro preprocesora.

W celu zapewnienia zgodności z poprzednimi wersjami `isascii` jest zaimplementowany jako makro tylko wtedy, gdy [&#95; &#95; STDC &#95; &#95; ](../../preprocessor/predefined-macros.md) nie został zdefiniowany lub jest zdefiniowany jako 0; w przeciwnym razie jest niezdefiniowany.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|`_istascii`|`__isascii`|`__isascii`|`iswascii`|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|`isascii`, `__isascii`|C: \<ctype.h ><br /><br /> C++: \<cctype — > lub \<ctype.h >|
|`iswascii`|C: \<wctype.h >, \<ctype.h >, lub \<wchar.h ><br /><br /> C++: \<cwctype — >, \<cctype — >, \<wctype.h >, \<ctype.h >, lub \<wchar.h >|

`isascii`, `__isascii` i `iswascii` funkcje są określone firmy Microsoft. Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md) we wprowadzeniu.

## <a name="see-also"></a>Zobacz też

[Klasyfikacja znaków](../../c-runtime-library/character-classification.md)   
[Ustawienia regionalne](../../c-runtime-library/locale.md)   
[jest isw — procedury](../../c-runtime-library/is-isw-routines.md)