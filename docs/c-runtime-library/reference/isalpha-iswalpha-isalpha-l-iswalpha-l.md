---
title: isalpha, iswalpha, _isalpha_l, _iswalpha_l
ms.date: 4/2/2020
api_name:
- iswalpha
- _iswalpha_l
- isalpha
- _isalpha_l
- _o_isalpha
- _o_iswalpha
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
ms.openlocfilehash: 187031adc0b22aff2c5418cd7e0f3e64075f1745
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81343927"
---
# <a name="isalpha-iswalpha-_isalpha_l-_iswalpha_l"></a>isalpha, iswalpha, _isalpha_l, _iswalpha_l

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

*C*<br/>
Całkowita ć do przetestowania.

*Ustawień regionalnych*<br/>
Ustawienia regionalne, które mają być używane zamiast bieżących ustawień regionalnych.

## <a name="return-value"></a>Wartość zwracana

Każda z tych procedur zwraca nonzero, jeśli *c* jest określoną reprezentacją znaku alfabetycznego. **isalpha** zwraca wartość niezerową, jeśli *c* znajduje się w zakresach A - Z lub a - z. **iswalpha** zwraca wartość różną od zera tylko dla szerokich znaków, dla których [iswupper](isupper-isupper-l-iswupper-iswupper-l.md) lub **iswlower** jest niezerowy; oznacza to, że dla każdego szerokiego znaku, który jest jednym z zestawu zdefiniowanego w implementacji, dla którego żaden z **iswcntrl**, **iswdigit**, **iswpunct**, lub **iswspace** jest nonzero. Każda z tych procedur zwraca wartość 0, jeśli *c* nie spełnia warunku badania.

Wersje tych funkcji, które mają sufiks **_l** używają parametru ustawień regionalnych, który jest przekazywany zamiast bieżących ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

Zachowanie **isalpha** i **_isalpha_l** jest niezdefiniowane, jeśli *c* nie jest EOF lub w zakresie od 0 do 0xFF, włącznie. Gdy biblioteka CRT debugowania jest używana i *c* nie jest jedną z tych wartości, funkcje podnieść potwierdzenia.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istalpha**|**isalpha**|**_ismbcalpha**|**iswalpha ( iswalpha )**|
|**_istalpha_l**|**_isalpha_l**|**_ismbcalpha_l**|**_iswalpha_l**|

## <a name="remarks"></a>Uwagi

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**isalpha**|\<ctype.h>|
|**iswalpha ( iswalpha )**|\<ctype.h> lub \<wchar.h>|
|**_isalpha_l**|\<ctype.h>|
|**_iswalpha_l**|\<ctype.h> lub \<wchar.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Klasyfikacja znaków](../../c-runtime-library/character-classification.md)<br/>
[Ustawienia regionalne](../../c-runtime-library/locale.md)<br/>
[is, isw, procedury](../../c-runtime-library/is-isw-routines.md)<br/>
