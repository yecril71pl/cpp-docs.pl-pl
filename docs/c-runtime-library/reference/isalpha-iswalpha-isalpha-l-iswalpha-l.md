---
title: isalpha, iswalpha, _isalpha_l, _iswalpha_l
ms.date: 11/04/2016
apiname:
- iswalpha
- _iswalpha_l
- isalpha
- _isalpha_l
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
- _istalpha
- _ismbcalpha_l
- isalpha
- _isalpha_l
- iswalpha
- _istalpha_l
- _iswalpha_l
helpviewer_keywords:
- _iswalpha_l function
- _isalpha_l function
- _ismbcalpha_l function
- _istalpha_l function
- _ismbcalpha function
- isalpha function
- iswalpha function
- istalpha function
- _istalpha function
ms.assetid: ed6cc2be-c4b0-4475-87ac-bc06d8c23064
ms.openlocfilehash: 47b7e43172884524e50e332dcb421e84a99b9806
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157997"
---
# <a name="isalpha-iswalpha-isalphal-iswalphal"></a>isalpha, iswalpha, _isalpha_l, _iswalpha_l

Określa, czy liczba całkowita reprezentuje znak alfabetyczny.

## <a name="syntax"></a>Składnia

```C
int isalpha(
   int c
);
int iswalpha(
   wint_t c
);
int _isalpha_l(
   int c,
   _locale_t locale
);
int _iswalpha_l(
   wint_t c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*c*<br/>
Liczba całkowita to testowania.

*Ustawienia regionalne*<br/>
Ustawienia regionalne, zamiast bieżących ustawień regionalnych.

## <a name="return-value"></a>Wartość zwracana

Każda z tych procedur zwraca wartość różną od zera, jeśli *c* jest szczególną reprezentacją znaku alfabetycznego. **isalpha** zwraca wartość różną od zera, jeśli *c* jest z zakresu A - Z lub a - z. **iswalpha —** zwraca wartość różną od zera dla znaków dwubajtowych, dla których [iswupper —](isupper-isupper-l-iswupper-iswupper-l.md) lub **iswlower —** jest różna od zera; tj dla dowolnego znaku dwubajtowego oznacza to jeden z zestawów zdefiniowanych w implementacji dla których żadna z **iswcntrl —**, **iswdigit —**, **iswpunct —**, lub **iswspace —** jest różna od zera. Każda z tych procedur zwraca 0, jeśli *c* nie spełnia warunku testowego.

Wersje tych funkcji, które mają **_l** sufiksa używa przekazanego parametru ustawień regionalnych, zamiast bieżących ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [ustawień regionalnych](../../c-runtime-library/locale.md).

Zachowanie **isalpha** i **_isalpha_l —** jest niezdefiniowane, jeżeli *c* nie jest równy EOF lub z zakresu od 0 do 0xFF włącznie. Jeśli jest używana biblioteka debugowania CRT i *c* nie jest jedną z tych wartości, funkcje wywołują potwierdzenie.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istalpha**|**isalpha**|**_ismbcalpha**|**iswalpha**|
|**_istalpha_l —**|**_isalpha_l**|**_ismbcalpha_l**|**_iswalpha_l —**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**isalpha**|\<ctype.h>|
|**iswalpha**|\<CType.h > lub \<wchar.h >|
|**_isalpha_l**|\<ctype.h>|
|**_iswalpha_l —**|\<CType.h > lub \<wchar.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Klasyfikacja znaków](../../c-runtime-library/character-classification.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[is, isw, procedury](../../c-runtime-library/is-isw-routines.md)<br/>
