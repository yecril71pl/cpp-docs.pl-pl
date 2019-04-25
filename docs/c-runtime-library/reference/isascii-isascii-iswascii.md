---
title: isascii, __isascii, iswascii
ms.date: 11/04/2016
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
helpviewer_keywords:
- __isascii function
- _isascii function
- isascii function
- _istascii function
- istascii function
- iswascii function
ms.assetid: ba4325ad-7cb3-4fb9-b096-58906d67971a
ms.openlocfilehash: d150e7bb335dc77ed86f445128eebf97b8be5ac3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62287472"
---
# <a name="isascii-isascii-iswascii"></a>isascii, __isascii, iswascii

Określa, czy określony znak jest znakiem ASCII.

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
Liczba całkowita to testowania.

## <a name="return-value"></a>Wartość zwracana

Każda z tych procedur zwraca wartość różną od zera, jeśli **c** jest szczególną reprezentacją znaku ASCII. **__isascii —** zwraca wartość różną od zera, jeśli **c** jest znak ASCII (z zakresu od 0x00 - 0x7F). **iswascii —** zwraca wartość różną od zera, jeśli **c** jest reprezentacją znaku dwubajtowego znaku ASCII. Każda z tych procedur zwraca 0, jeśli **c** nie spełnia warunku testowego.

## <a name="remarks"></a>Uwagi

Zarówno **__isascii —** i **iswascii —** są implementowane jako makra, chyba że _CTYPE_DISABLE_MACROS makro preprocesora jest zdefiniowana.

W celu zapewnienia zgodności z poprzednimi wersjami **isascii —** jest implementowany jako makra tylko wtedy, gdy [ &#95; &#95;STDC&#95; &#95; ](../../preprocessor/predefined-macros.md) nie został zdefiniowany lub jest zdefiniowana jako 0; w przeciwnym razie jest niezdefiniowany.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_istascii**|**__isascii**|**__isascii**|**iswascii**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**isascii —**, **__isascii —**|C: \<ctype.h><br /><br /> C++: \<cctype — > lub \<ctype.h >|
|**iswascii**|C: \<wctype.h >, \<ctype.h >, lub \<wchar.h ><br /><br /> C++: \<cwctype — >, \<cctype — >, \<wctype.h >, \<ctype.h >, lub \<wchar.h >|

**Isascii —**, **__isascii —** i **iswascii —** funkcje są specyficzne dla firmy Microsoft. Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Klasyfikacja znaków](../../c-runtime-library/character-classification.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[is, isw, procedury](../../c-runtime-library/is-isw-routines.md)<br/>
