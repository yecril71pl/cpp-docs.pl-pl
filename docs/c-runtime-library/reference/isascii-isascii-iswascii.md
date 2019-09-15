---
title: isascii, __isascii, iswascii
ms.date: 11/04/2016
api_name:
- iswascii
- __isascii
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
- api-ms-win-crt-string-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- iswascii
- istascii
- __isascii
- _istascii
- isascii
- ctype/isascii
- ctype/__isascii
- corecrt_wctype/iswascii
helpviewer_keywords:
- __isascii function
- _isascii function
- isascii function
- _istascii function
- istascii function
- iswascii function
ms.assetid: ba4325ad-7cb3-4fb9-b096-58906d67971a
ms.openlocfilehash: ee20711628d5c2135b4ee1c37b87cb77f3610695
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954570"
---
# <a name="isascii-__isascii-iswascii"></a>isascii, __isascii, iswascii

Określa, czy konkretny znak jest znakiem ASCII.

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

*c*<br/>
Liczba całkowita do przetestowania.

## <a name="return-value"></a>Wartość zwracana

Każda z tych procedur zwraca wartość różną od zera, jeśli **c** jest szczególną reprezentacją znaku ASCII. **__isascii** zwraca wartość różną od zera, jeśli **c** jest znakiem ASCII (w zakresie 0x00-0x7F). **iswascii** zwraca wartość różną od zera, jeśli **c** jest reprezentacją dwubajtowego znaku ASCII. Każda z tych procedur zwraca wartość 0, jeśli **c** nie spełnia warunku testu.

## <a name="remarks"></a>Uwagi

Zarówno **__isascii** , jak i **iswascii** są zaimplementowane jako makra, chyba że zdefiniowano _CTYPE_DISABLE_MACROS makro preprocesora.

W celu zapewnienia zgodności z poprzednimi wersjami program **isascii** jest implementowany jako makro tylko wtedy, gdy [ &#95; &#95;STDC&#95; ](../../preprocessor/predefined-macros.md) nie jest zdefiniowany lub jest zdefiniowany jako 0; w przeciwnym razie jest to niezdefiniowane.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_istascii**|**__isascii**|**__isascii**|**iswascii**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**isascii**, **__isascii**|C: \<CType. h ><br /><br /> C++: \<cctype > lub \<CType. h >|
|**iswascii**|C: \<wctype. h >, \<CType. h > lub \<WCHAR. h ><br /><br /> C++: \<cwctype >, \<cctype >, \<wctype. h >, \<CType. h > lub \<WCHAR. h >|

Funkcje **isascii**, **__isascii** i **Iswascii** są specyficzne dla firmy Microsoft. Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Klasyfikacja znaków](../../c-runtime-library/character-classification.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[is, isw, procedury](../../c-runtime-library/is-isw-routines.md)<br/>
