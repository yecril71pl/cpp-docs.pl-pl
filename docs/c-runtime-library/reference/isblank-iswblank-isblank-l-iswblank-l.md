---
title: isblank, iswblank, _isblank_l, _iswblank_l
ms.date: 11/04/2016
api_name:
- isblank
- _isblank_l
- iswblank
- _iswblank_l
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
- _iswblank_l
- isblank
- _istblank_l
- _istblank
- _isblank_l
- iswblank
ms.assetid: 33ce96c0-f387-411a-8283-c3d2a69e56bd
ms.openlocfilehash: 022eba0335facc597f0608d63cfb58e0146e0f23
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954519"
---
# <a name="isblank-iswblank-_isblank_l-_iswblank_l"></a>isblank, iswblank, _isblank_l, _iswblank_l

Określa, czy liczba całkowita reprezentuje znak pusty.

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
Liczba całkowita do przetestowania.

*ustawienie*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Każda z tych procedur zwraca wartość różną od zera, jeśli *c* jest szczególną reprezentacją znaku spacji lub tabulatora poziomego lub jest jednym z zestawów znaków specyficznych dla ustawień regionalnych, które są używane do oddzielania słów w wierszu tekstu. Funkcja **ISBLANK** zwraca wartość różną od zera, jeśli *c* jest znakiem spacji (0x20) lub tabulatorem poziomym (0x09). Wynik warunku testowego dla funkcji **ISBLANK** zależy od ustawienia kategorii **LC_CTYPE** ustawień regionalnych; Aby uzyskać więcej informacji, zobacz [setlocals, _wsetlocale](setlocale-wsetlocale.md). Wersje tych funkcji, które nie mają sufiksu **_l** , używają bieżących ustawień regionalnych dla wszelkich zachowań zależnych od ustawień regionalnych. wersje, które mają sufiks **_l** są identyczne, z tą różnicą, że używają zamiast nich ustawień regionalnych, które zostały przesłane. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

**iswblank** zwraca wartość różną od zera, jeśli *c* jest znakiem dwubajtowym, który odnosi się do obszaru standardowego lub tabulatora poziomego.

Zachowanie funkcji **ISBLANK** i **_isblank_l** jest niezdefiniowane, jeśli *c* nie jest typu EOF lub z zakresu od 0 do 0xFF włącznie. Gdy jest używana Biblioteka CRT debugowania, a *c* nie jest jedną z tych wartości, funkcje zgłaszają potwierdzenie.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _UNICODE & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istblank**|**isblank**|[_ismbcblank](ismbcgraph-functions.md)|**iswblank**|
|**_istblank_l**|**_isblank_l**|[_ismbcblank_l](ismbcgraph-functions.md)|**_iswblank_l**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**isblank**|\<ctype.h>|
|**iswblank**|\<CType. h > lub \<WCHAR. h >|
|**_isblank_l**|\<ctype.h>|
|**_iswblank_l**|\<CType. h > lub \<WCHAR. h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Klasyfikacja znaków](../../c-runtime-library/character-classification.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[is, isw, procedury](../../c-runtime-library/is-isw-routines.md)<br/>
