---
title: ispunct, iswpunct, _ispunct_l, _iswpunct_l
ms.date: 11/04/2016
api_name:
- ispunct
- _iswpunct_l
- iswpunct
- _ispunct_l
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
ms.openlocfilehash: 54c51c612cf3b491b49d7e141df34ed5b4415520
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953700"
---
# <a name="ispunct-iswpunct-_ispunct_l-_iswpunct_l"></a>ispunct, iswpunct, _ispunct_l, _iswpunct_l

Określa, czy liczba całkowita reprezentuje znak interpunkcji.

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

*c*<br/>
Liczba całkowita do przetestowania.

*ustawienie*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Każda z tych procedur zwraca wartość różną od zera, jeśli *c* jest szczególną reprezentacją znaku interpunkcji. **ispunct** zwraca wartość różną od zera dla dowolnego znaku drukowalnego, który nie jest znakiem spacji ani znakiem, dla którego **isalnum** jest różna od zera. **iswpunct** zwraca wartość różną od zera dla dowolnego drukowalnego znaku dwubajtowego, który nie jest znakiem szerokości odstępu ani znakiem dwubajtowym, dla którego **iswalnum** jest różna od zera. Każda z tych procedur zwraca wartość 0, jeśli *c* nie spełnia warunku testu.

Wynik warunku testowego dla funkcji **ispunct** zależy od ustawienia kategorii **LC_CTYPE** ustawień regionalnych; Zobacz [setlocaling, _wsetlocale,](setlocale-wsetlocale.md) Aby uzyskać więcej informacji. Wersje tych funkcji, które nie mają sufiksu **_l** , używają bieżących ustawień regionalnych dla wszelkich zachowań zależnych od ustawień regionalnych. wersje, które mają sufiks **_l** są identyczne, z tą różnicą, że używają zamiast nich ustawień regionalnych, które zostały przesłane. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

Zachowanie **ispunct** i **_ispunct_l** jest niezdefiniowane, jeśli *c* nie jest typu EOF lub z zakresu od 0 do 0xFF włącznie. Gdy jest używana Biblioteka CRT debugowania, a *c* nie jest jedną z tych wartości, funkcje zgłaszają potwierdzenie.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _UNICODE & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_** **istpunct**|**ispunct**|[_ismbcpunct](ismbcgraph-functions.md)|**iswpunct**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**ispunct**|\<ctype.h>|
|**iswpunct**|\<CType. h > lub \<WCHAR. h >|
|**_ispunct_l**|\<ctype.h>|
|**_iswpunct_l**|\<CType. h > lub \<WCHAR. h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Klasyfikacja znaków](../../c-runtime-library/character-classification.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[is, isw, procedury](../../c-runtime-library/is-isw-routines.md)<br/>
