---
title: ISBLANK, iswblank, _isblank_l, _iswblank_l | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- isblank
- _isblank_l
- iswblank
- _iswblank_l
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
- _iswblank_l
- isblank
- _istblank_l
- _istblank
- _isblank_l
- iswblank
dev_langs:
- C++
ms.assetid: 33ce96c0-f387-411a-8283-c3d2a69e56bd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d2787be85aa4e12bf22d1be14f90568891b83824
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32403316"
---
# <a name="isblank-iswblank-isblankl-iswblankl"></a>isblank, iswblank, _isblank_l, _iswblank_l

Określa, czy liczba całkowita reprezentuje pusty znak.

## <a name="syntax"></a>Składnia

```C
int isblank(
   int c
);
int iswblank(
   wint_t c
);
int _isblank_l(
   int c,
   _locale_t locale
);
int _iswblank_l(
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

Każdy z tych procedur zwraca różną od zera, jeśli *c* jest reprezentację określonego obiektu spację lub tabulator poziomy lub jednego z ustawień regionalnych zestaw znaków, które są używane do oddzielania słów w wierszu tekstu. **ISBLANK** zwraca wartość niezerową, jeśli *c* jest znak spacji (0x20) lub tabulator poziomy znaków (0x09). Wynik testu warunku **isblank** zależy od funkcji **lc_ctype —** kategorii ustawienie ustawień regionalnych; Aby uzyskać więcej informacji, zobacz [setlocale, _wsetlocale —](setlocale-wsetlocale.md). Wersje tych funkcji, które nie mają **_l** sufiks użyciem bieżących ustawień regionalnych wszystkie działania zależne od ustawień regionalnych; wersje, które mają **_l** sufiks są identyczne z tą różnicą, że używają one Ustawienia regionalne jest przekazywany w zamian. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

**iswblank** zwraca wartość niezerową, jeśli *c* znaków dwubajtowych, umożliwiająca miejsce na standardowej lub tabulator poziomy.

Zachowanie **isblank** i **_isblank_l** jest niezdefiniowana, jeśli *c* nie jest EOF lub w zakresie od 0 do 0xFF włącznie. Gdy zostanie użyty bibliotek debugowania CRT i *c* nie jest jedną z tych wartości, zgłoś funkcje potwierdzenia.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istblank**|**isblank**|[_ismbcblank](ismbcgraph-functions.md)|**iswblank**|
|**_istblank_l**|**_isblank_l**|[_ismbcblank_l](ismbcgraph-functions.md)|**_iswblank_l**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**isblank**|\<ctype.h>|
|**iswblank**|\<CType.h > lub \<wchar.h >|
|**_isblank_l**|\<ctype.h>|
|**_iswblank_l**|\<CType.h > lub \<wchar.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Klasyfikacja znaków](../../c-runtime-library/character-classification.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[is, isw, procedury](../../c-runtime-library/is-isw-routines.md)<br/>
