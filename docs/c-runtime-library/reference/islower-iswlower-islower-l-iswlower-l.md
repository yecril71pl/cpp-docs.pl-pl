---
title: islower —, iswlower —, _islower_l —, _iswlower_l — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- iswlower
- _islower_l
- islower
- _iswlower_l
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
- _istlower
- islower
- _ismbclower_l
- _liswlower_l
- _istlower_l
- _iswlower_l
- _islower _l
- _islower_l
- iswlower
dev_langs:
- C++
helpviewer_keywords:
- _islower _l function
- _ismbclower_l function
- islower function
- _iswlower_l function
- _liswlower_l function
- _istlower_l function
- istlower function
- _istlower function
- iswlower function
- _islower_l function
ms.assetid: fcc3b70a-2b47-45fd-944d-e5c1942e6457
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 14fb6eae9e06e973413c21607f2ca2881f33aa38
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32401834"
---
# <a name="islower-iswlower-islowerl-iswlowerl"></a>islower, iswlower, _islower_l, _iswlower_l

Określa, czy liczba całkowita reprezentuje małą literę.

## <a name="syntax"></a>Składnia

```C
int islower(
   int c
);
int iswlower(
   wint_t c
);
int islower_l(
   int c,
   _locale_t locale
);
int _iswlower_l(
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

Każdy z tych procedur zwraca różną od zera, jeśli *c* jest reprezentację określonego obiektu małą literę. **islower —** zwraca wartość niezerową, jeśli *c* jest małą literę (- z). **iswlower —** zwraca wartość niezerową, jeśli *c* jest znaków dwubajtowych, umożliwiająca małe litery, lub jeśli *c* jest jednym z zestawu znaki dwubajtowe zdefiniowane w implementacji dla których żadna **iswcntrl —**, **iswdigit —**, **iswpunct —**, lub **iswspace —** jest różna od zera. Każdy z tych procedur zwraca 0, jeśli *c* nie spełnia warunku.

Wersje tych funkcji, które mają **_l** sufiks Użyj ustawień regionalnych, który jest przekazywany w zamiast bieżące ustawienia regionalne dla ich działania zależnego od ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

Zachowanie **islower —** i **_islower_l —** jest niezdefiniowana, jeśli *c* nie jest EOF lub w zakresie od 0 do 0xFF włącznie. Gdy zostanie użyty bibliotek debugowania CRT i *c* nie jest jedną z tych wartości, zgłoś funkcje potwierdzenia.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istlower —**|**islower**|[_ismbclower](ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|**iswlower**|
|**_istlower_l —**|`_islower _l`|[_ismbclower_l](ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|**_liswlower_l —**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**islower**|\<ctype.h>|
|**iswlower**|\<CType.h > lub \<wchar.h >|
|**_islower_l**|\<ctype.h>|
|**_swlower_l**|\<CType.h > lub \<wchar.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Klasyfikacja znaków](../../c-runtime-library/character-classification.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[is, isw, procedury](../../c-runtime-library/is-isw-routines.md)<br/>
