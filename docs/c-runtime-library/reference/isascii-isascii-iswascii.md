---
title: isascii, __isascii, iswascii
ms.date: 4/2/2020
api_name:
- iswascii
- __isascii
- _o_iswascii
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: aeb9c27fee4d179cc16caa50c6f0aae521402beb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81343910"
---
# <a name="isascii-__isascii-iswascii"></a>isascii, __isascii, iswascii

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

*C*<br/>
Całkowita ć do przetestowania.

## <a name="return-value"></a>Wartość zwracana

Każda z tych procedur zwraca nonzero, jeśli **c** jest określoną reprezentacją znaku ASCII. **__isascii** zwraca wartość niezerową, jeśli **c** jest znakiem ASCII (w zakresie 0x00 - 0x7F). **iswascii** zwraca wartość różną od zera, jeśli **c** jest szeroką reprezentacją znaku ASCII. Każda z tych procedur zwraca wartość 0, jeśli **c** nie spełnia warunku badania.

## <a name="remarks"></a>Uwagi

Zarówno **__isascii,** jak i **iswascii** są implementowane jako makra, chyba że zdefiniowano _CTYPE_DISABLE_MACROS makra preprocesora.

W przypadku zgodności z powrotem **isascii** jest implementowane jako makro tylko wtedy, [gdy&#95;&#95;&#95;&#95;STDC](../../preprocessor/predefined-macros.md) nie jest zdefiniowany lub jest zdefiniowany jako 0; w przeciwnym razie jest niezdefiniowany.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_istascii**|**__isascii**|**__isascii**|**iswascii ( iswascii )**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**isascii**, **__isascii**|C: \<ctype.h><br /><br /> C++: \<cctype> lub \<ctype.h>|
|**iswascii ( iswascii )**|C: \<wctype.h>, \<ctype.h> lub \<wchar.h><br /><br /> C++: \<cwctype>, \<cctype>, \<wctype.h>, \<ctype.h> lub \<wchar.h>|

Funkcje **isascii**, **__isascii** i **iswascii** są specyficzne dla firmy Microsoft. Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Klasyfikacja znaków](../../c-runtime-library/character-classification.md)<br/>
[Ustawienia regionalne](../../c-runtime-library/locale.md)<br/>
[is, isw, procedury](../../c-runtime-library/is-isw-routines.md)<br/>
