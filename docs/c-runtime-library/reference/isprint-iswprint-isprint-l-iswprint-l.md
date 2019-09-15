---
title: isprint, iswprint, _isprint_l, _iswprint_l
ms.date: 11/04/2016
api_name:
- iswprint
- isprint
- _isprint_l
- _iswprint_l
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
ms.openlocfilehash: 282b72fcec84f8096ce0d54cd114e756aeafbc85
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953746"
---
# <a name="isprint-iswprint-_isprint_l-_iswprint_l"></a>isprint, iswprint, _isprint_l, _iswprint_l

Określa, czy liczba całkowita reprezentuje Znak drukowalny.

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

*c*<br/>
Liczba całkowita do przetestowania.

*ustawienie*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Każda z tych procedur zwraca wartość różną od zera, jeśli *c* jest szczególną reprezentacją znaku drukowalnego. Funkcja **isprint** zwraca wartość różną od zera, jeśli *c* jest znakiem drukowalnym — obejmuje to znak spacji (0x20-0x7E). **iswprint** zwraca wartość różną od zera, jeśli *c* jest znakiem dwubajtowym, co obejmuje znak odstępu. Każda z tych procedur zwraca wartość 0, jeśli *c* nie spełnia warunku testu.

Wynik warunku testowego dla tych funkcji zależy od ustawienia kategorii **LC_CTYPE** ustawień regionalnych; Zobacz [setlocaling, _wsetlocale,](setlocale-wsetlocale.md) Aby uzyskać więcej informacji. Wersje tych funkcji, które nie mają sufiksu **_l** , używają bieżących ustawień regionalnych dla wszelkich zachowań zależnych od ustawień regionalnych. wersje, które mają sufiks **_l** są identyczne, z tą różnicą, że używają zamiast nich ustawień regionalnych, które zostały przesłane. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

Zachowanie elementu **isprint** i **_isprint_l** jest niezdefiniowane, jeśli *c* nie jest typu EOF lub z zakresu od 0 do 0xFF włącznie. Gdy jest używana Biblioteka CRT debugowania, a *c* nie jest jedną z tych wartości, funkcje zgłaszają potwierdzenie.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _UNICODE & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowany|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_** **istprint**|**isprint**|[_ismbcprint](ismbcgraph-functions.md)|**iswprint**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**isprint**|\<ctype.h>|
|**iswprint**|\<CType. h > lub \<WCHAR. h >|
|**_isprint_l**|\<ctype.h>|
|**_iswprint_l**|\<CType. h > lub \<WCHAR. h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Klasyfikacja znaków](../../c-runtime-library/character-classification.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[is, isw, procedury](../../c-runtime-library/is-isw-routines.md)<br/>
