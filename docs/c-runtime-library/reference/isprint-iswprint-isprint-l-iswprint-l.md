---
title: isprint, iswprint, _isprint_l, _iswprint_l
ms.date: 4/2/2020
api_name:
- iswprint
- isprint
- _isprint_l
- _iswprint_l
- _o_isprint
- _o_iswprint
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
- iswprint
- _istprint
- isprint
helpviewer_keywords:
- _istprint function
- iswprint function
- _iswprint_l function
- isprint_l function
- istprint function
- isprint function
- iswprint_l function
- _isprint_l function
ms.assetid: a8bbcdb0-e8d0-4d8c-ae4e-56d3bdee6ca3
ms.openlocfilehash: f09168e8e010fb59d748c109d4a41c533318e2eb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342882"
---
# <a name="isprint-iswprint-_isprint_l-_iswprint_l"></a>isprint, iswprint, _isprint_l, _iswprint_l

Określa, czy liczba całkowita reprezentuje znak do wydrukowania.

## <a name="syntax"></a>Składnia

```C
int isprint(
   int c
);
int iswprint(
   wint_t c
);
int _isprint_l(
   int c,
   _locale_t locale
);
int _iswprint_l(
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

Każda z tych procedur zwraca wartość niezerową, jeśli *c* jest określoną reprezentacją znaku drukowalnej. **isprint** zwraca wartość niezerową, jeśli *c* jest znakiem do wydrukowania — obejmuje znak spacji (0x20 - 0x7E). **iswprint** zwraca wartość różną od zera, jeśli *c* jest znakiem szerokiego drukowania — obejmuje to znak szerokiej przestrzeni. Każda z tych procedur zwraca wartość 0, jeśli *c* nie spełnia warunku badania.

Wynik warunku testu dla tych funkcji zależy od **LC_CTYPE** ustawienie kategorii ustawień regionalnych; zobacz [setlocale, _wsetlocale aby](setlocale-wsetlocale.md) uzyskać więcej informacji. Wersje tych funkcji, które nie mają sufiksu **_l,** używają bieżących ustawień regionalnych dla zachowania zależnego od ustawień regionalnych; wersje, które mają **_l** sufiks są identyczne, z tą różnicą, że używają ustawień regionalnych, które są przekazywane zamiast. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

Zachowanie **isprint** i **_isprint_l** jest niezdefiniowana, jeśli *c* nie jest EOF lub w zakresie od 0 do 0xFF włącznie. Gdy biblioteka CRT debugowania jest używana i *c* nie jest jedną z tych wartości, funkcje podnieść potwierdzenia.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_unicode zdefiniowane|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_** **istprint**|**isprint**|[_ismbcprint](ismbcgraph-functions.md)|**druk iswprint**|

## <a name="remarks"></a>Uwagi

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**isprint**|\<ctype.h>|
|**druk iswprint**|\<ctype.h> lub \<wchar.h>|
|**_isprint_l**|\<ctype.h>|
|**_iswprint_l**|\<ctype.h> lub \<wchar.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Klasyfikacja znaków](../../c-runtime-library/character-classification.md)<br/>
[Ustawienia regionalne](../../c-runtime-library/locale.md)<br/>
[is, isw, procedury](../../c-runtime-library/is-isw-routines.md)<br/>
