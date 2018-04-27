---
title: ispunct —, iswpunct —, _ispunct_l —, _iswpunct_l — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ispunct
- _iswpunct_l
- iswpunct
- _ispunct_l
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
- iswpunct
- _istpunct
- ispunct
dev_langs:
- C++
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
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 22240d2d13781a77dd99afd215f5ee5677b62cc4
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="ispunct-iswpunct-ispunctl-iswpunctl"></a>ispunct, iswpunct, _ispunct_l, _iswpunct_l

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

*c*<br/>
Liczba całkowita do testowania.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Każdy z tych procedur zwraca różną od zera, jeśli *c* jest reprezentację określonego obiektu znak interpunkcyjny. **ispunct —** zwraca wartość niezerową dowolny znak drukowania, który nie jest znak spacji ani znaków, dla którego **isalnum —** jest różna od zera. **iswpunct —** zwraca wartość niezerową drukowalnych znaków dwubajtowych, który nie jest znaku dwubajtowe spacji ani znaków dwubajtowych, dla którego **iswalnum —** jest różna od zera. Każdy z tych procedur zwraca 0, jeśli *c* nie spełnia warunku.

Wynik testu warunku **ispunct —** zależy od funkcji **lc_ctype —** ustawienie kategorii ustawień regionalnych; zobacz [setlocale, _wsetlocale —](setlocale-wsetlocale.md) Aby uzyskać więcej informacji. Wersje tych funkcji, które nie mają **_l** sufiks użyciem bieżących ustawień regionalnych wszystkie działania zależne od ustawień regionalnych; wersje, które mają **_l** sufiks są identyczne z tą różnicą, że używają one Ustawienia regionalne jest przekazywany w zamian. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

Zachowanie **ispunct —** i **_ispunct_l —** jest niezdefiniowana, jeśli *c* nie jest EOF lub w zakresie od 0 do 0xFF włącznie. Gdy zostanie użyty bibliotek debugowania CRT i *c* nie jest jedną z tych wartości, zgłoś funkcje potwierdzenia.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_** **istpunct —**|**ispunct —**|[_ismbcpunct](ismbcgraph-functions.md)|**iswpunct**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**ispunct —**|\<ctype.h>|
|**iswpunct**|\<CType.h > lub \<wchar.h >|
|**_ispunct_l**|\<ctype.h>|
|**_iswpunct_l**|\<CType.h > lub \<wchar.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Klasyfikacja znaków](../../c-runtime-library/character-classification.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[is, isw, procedury](../../c-runtime-library/is-isw-routines.md)<br/>
