---
title: ispunct, iswpunct, _ispunct_l, _iswpunct_l
ms.date: 4/2/2020
api_name:
- ispunct
- _iswpunct_l
- iswpunct
- _ispunct_l
- _o_ispunct
- _o_iswpunct
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
- iswpunct
- _istpunct
- ispunct
helpviewer_keywords:
- _istpunct function
- _ispunct_l function
- iswpunct function
- ispunct function
- istpunct function
- ispunct_l function
- _iswpunct_l function
- iswpunct_l function
ms.assetid: 94403240-85c8-40a4-9c2b-e3e95c729c76
ms.openlocfilehash: 3072f147d2adff2c50304d2d2052947ca32cb060
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342808"
---
# <a name="ispunct-iswpunct-_ispunct_l-_iswpunct_l"></a>ispunct, iswpunct, _ispunct_l, _iswpunct_l

Określa, czy liczba całkowita reprezentuje znak interpunkcyjny.

## <a name="syntax"></a>Składnia

```C
int ispunct(
   int c
);
int iswpunct(
   wint_t c
);
int _ispunct_l(
   int c,
   _locale_t locale
);
int _iswpunct_l(
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

Każda z tych procedur zwraca nonzero, jeśli *c* jest określoną reprezentacją znaku interpunkcyjnego. **ispunct** zwraca wartość niezerową dla dowolnego znaku drukowalnej, który nie jest znakiem spacji lub znakiem, dla którego **isalnum** jest niezerowy. **iswpunct** zwraca wartość różną od zera dla dowolnego drukowanego znaku szerokiego, który nie jest ani znakiem szerokości przestrzeni, ani szerokim znakiem, dla którego **iswalnum** jest niezerowy. Każda z tych procedur zwraca wartość 0, jeśli *c* nie spełnia warunku badania.

Wynik stanu badania dla funkcji **izpunek** zależy od **LC_CTYPE** ustawienie kategorii ustawień regionalnych; zobacz [setlocale, _wsetlocale aby](setlocale-wsetlocale.md) uzyskać więcej informacji. Wersje tych funkcji, które nie mają sufiksu **_l,** używają bieżących ustawień regionalnych dla zachowania zależnego od ustawień regionalnych; wersje, które mają **_l** sufiks są identyczne, z tą różnicą, że używają ustawień regionalnych, które są przekazywane zamiast. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

Zachowanie **ipunktu** i **_ispunct_l** jest niezdefiniowane, jeśli *c* nie jest EOF lub w zakresie od 0 do 0xFF włącznie. Gdy biblioteka CRT debugowania jest używana i *c* nie jest jedną z tych wartości, funkcje podnieść potwierdzenia.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_** **istpunct**|**ispunct**|[_ismbcpunct](ismbcgraph-functions.md)|**punktowania**|

## <a name="remarks"></a>Uwagi

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**ispunct**|\<ctype.h>|
|**punktowania**|\<ctype.h> lub \<wchar.h>|
|**_ispunct_l**|\<ctype.h>|
|**_iswpunct_l**|\<ctype.h> lub \<wchar.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Klasyfikacja znaków](../../c-runtime-library/character-classification.md)<br/>
[Ustawienia regionalne](../../c-runtime-library/locale.md)<br/>
[is, isw, procedury](../../c-runtime-library/is-isw-routines.md)<br/>
