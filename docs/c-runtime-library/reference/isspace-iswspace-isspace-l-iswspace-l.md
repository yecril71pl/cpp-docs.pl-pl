---
title: isspace, iswspace, _isspace_l, _iswspace_l
ms.date: 11/04/2016
apiname:
- iswspace
- _isspace_l
- _iswspace_l
- isspace
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
ms.openlocfilehash: cd93b196c23be5e91852e8c02d75055c1051b912
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50590461"
---
# <a name="isspace-iswspace-isspacel-iswspacel"></a>isspace, iswspace, _isspace_l, _iswspace_l

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

*c*<br/>
Liczba całkowita to testowania.

*Ustawienia regionalne*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Każda z tych procedur zwraca wartość różną od zera, jeśli *c* jest szczególną reprezentacją znaku spacji. **isspace** zwraca wartość różną od zera, jeśli *c* jest znakiem spacji (0x09 — 0x0D lub 0x20). Wynik warunku testowego dla **isspace** zależy od funkcji **LC_CTYPE** ustawienia kategorii ustawień regionalnych; zobacz [setlocale, _wsetlocale](setlocale-wsetlocale.md) Aby uzyskać więcej informacji. Wersje tych funkcji, które nie mają **_l** sufiks Użyj bieżących ustawień regionalnych dla wszelkich zachowań zależnych od ustawień regionalnych; wersje, które mają **_l** sufiksem są identyczne, z tą różnicą, że używają one Ustawienia regionalne, który jest przekazywany zamiast tego. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

**iswspace —** zwraca wartość różną od zera, jeśli *c* jest znakiem dwubajtowym, który odnosi się do standardowych znaków spacji.

Zachowanie **isspace** i **_isspace_l —** jest niezdefiniowane, jeżeli *c* nie jest równy EOF lub z zakresu od 0 do 0xFF włącznie. Jeśli jest używana biblioteka debugowania CRT i *c* nie jest jedną z tych wartości, funkcje wywołują potwierdzenie.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_** **istspace —**|**isspace**|[_ismbcspace](ismbcgraph-functions.md)|**iswspace**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**isspace**|\<ctype.h>|
|**iswspace**|\<CType.h > lub \<wchar.h >|
|**_isspace_l**|\<ctype.h>|
|**_iswspace_l**|\<CType.h > lub \<wchar.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Klasyfikacja znaków](../../c-runtime-library/character-classification.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[is, isw, procedury](../../c-runtime-library/is-isw-routines.md)<br/>
