---
title: isspace, iswspace, _isspace_l, _iswspace_l
ms.date: 4/2/2020
api_name:
- iswspace
- _isspace_l
- _iswspace_l
- isspace
- _o_isspace
- _o_iswspace
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
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- iswspace
- _istspace
- isspace
helpviewer_keywords:
- iswspace function
- isspace function
- _iswspace_l function
- _isspace_l function
- iswspace_l function
- isspace_l function
- _istspace function
- istspace function
ms.assetid: b851e0c0-36bb-4dac-a1a3-533540939035
ms.openlocfilehash: 43d66a191427e886941fd3dcac5dc6b71146b68a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342760"
---
# <a name="isspace-iswspace-_isspace_l-_iswspace_l"></a>isspace, iswspace, _isspace_l, _iswspace_l

Określa, czy liczba całkowita reprezentuje znak spacji.

## <a name="syntax"></a>Składnia

```C
int isspace(
   int c
);
int iswspace(
   wint_t c
);
int _isspace_l(
   int c,
   _locale_t locale
);
int _iswspace_l(
   wint_t c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*C*<br/>
Całkowita ć do przetestowania.

*Ustawień regionalnych*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Każda z tych procedur zwraca nonzero, jeśli *c* jest określoną reprezentacją znaku spacji. **isspace** zwraca wartość różną od zera, jeśli *c* jest znakiem odstępu (0x09 - 0x0D lub 0x20). Wynik warunku testu dla funkcji **isspace** zależy od **ustawienia kategorii LC_CTYPE** ustawień ustawień regionalnych; zobacz [setlocale, _wsetlocale aby](setlocale-wsetlocale.md) uzyskać więcej informacji. Wersje tych funkcji, które nie mają sufiksu **_l,** używają bieżących ustawień regionalnych dla zachowania zależnego od ustawień regionalnych; wersje, które mają **_l** sufiks są identyczne, z tą różnicą, że używają ustawień regionalnych, które są przekazywane zamiast. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

**iswspace** zwraca wartość różną od zera, jeśli *c* jest szerokim znakiem odpowiadającym standardowemu znakowi odstępu.

Zachowanie **isspace** i **_isspace_l** jest niezdefiniowana, jeśli *c* nie jest EOF lub w zakresie od 0 do 0xFF włącznie. Gdy biblioteka CRT debugowania jest używana i *c* nie jest jedną z tych wartości, funkcje podnieść potwierdzenia.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_** **istspace (istspace)**|**obszar isspace**|[_ismbcspace](ismbcgraph-functions.md)|**iswspace (przestrzeń kosmiczna)**|

## <a name="remarks"></a>Uwagi

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**obszar isspace**|\<ctype.h>|
|**iswspace (przestrzeń kosmiczna)**|\<ctype.h> lub \<wchar.h>|
|**_isspace_l**|\<ctype.h>|
|**_iswspace_l**|\<ctype.h> lub \<wchar.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Klasyfikacja znaków](../../c-runtime-library/character-classification.md)<br/>
[Ustawienia regionalne](../../c-runtime-library/locale.md)<br/>
[is, isw, procedury](../../c-runtime-library/is-isw-routines.md)<br/>
