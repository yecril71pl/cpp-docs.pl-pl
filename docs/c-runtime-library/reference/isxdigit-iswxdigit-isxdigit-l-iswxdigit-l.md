---
title: isxdigit, iswxdigit, _isxdigit_l, _iswxdigit_l
ms.date: 4/2/2020
api_name:
- _iswxdigit_l
- iswxdigit
- isxdigit
- _isxdigit_l
- _o_iswxdigit
- _o_isxdigit
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- iswxdigit
- isxdigit
- _istxdigit
helpviewer_keywords:
- isxdigit function
- istxdigit function
- _iswxdigit_l function
- _istxdigit function
- _isxdigit_l function
- iswxdigit_l function
- isxdigit_l function
- hexadecimal characters
- iswxdigit function
ms.assetid: c8bc5146-0b58-4e3f-bee3-f2318dd0f829
ms.openlocfilehash: 3aefa39d9fabb2b8a3124955f3ab0787e9e174f3
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82916585"
---
# <a name="isxdigit-iswxdigit-_isxdigit_l-_iswxdigit_l"></a>isxdigit, iswxdigit, _isxdigit_l, _iswxdigit_l

Określa, czy liczba całkowita reprezentuje znak, który jest cyfrą szesnastkową.

## <a name="syntax"></a>Składnia

```C
int isxdigit(
   int c
);
int iswxdigit(
   wint_t c
);
int _isxdigit_l(
   int c,
   _locale_t locale
);
int _iswxdigit_l(
   wint_t c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*s*<br/>
Liczba całkowita do przetestowania.

*locale*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Każda z tych procedur zwraca wartość różną od zera, jeśli *c* jest szczególną reprezentacją cyfry szesnastkowej. **isxdigit** zwraca wartość różną od zera, jeśli *c* jest cyfrą szesnastkową (a-f, a-f lub 0-9). **iswxdigit** zwraca wartość różną od zera, jeśli *c* jest znakiem dwubajtowym, który odpowiada znakowi cyfry szesnastkowej. Każda z tych procedur zwraca wartość 0, jeśli *c* nie spełnia warunku testu.

Dla ustawień regionalnych "C" funkcja **iswxdigit** nie obsługuje znaków szesnastkowych o pełnej szerokości Unicode.

Wersje tych funkcji, które mają sufiks **_l** używają ustawień regionalnych, które zostały przesłane zamiast bieżących ustawień regionalnych dla zachowań zależnych od ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

Zachowanie **isxdigit** i **_isxdigit_l** jest niezdefiniowane, jeśli *c* nie jest typu EOF lub z zakresu od 0 do 0xFF włącznie. Gdy jest używana Biblioteka CRT debugowania, a *c* nie jest jedną z tych wartości, funkcje zgłaszają potwierdzenie.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _MBCS _UNICODE &|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istxdigit**|**isxdigit**|**isxdigit**|**iswxdigit**|

## <a name="remarks"></a>Uwagi

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**isxdigit**|\<CType. h>|
|**iswxdigit**|\<CType. h> lub \<WCHAR. h>|
|**_isxdigit_l**|\<CType. h>|
|**_iswxdigit_l**|\<CType. h> lub \<WCHAR. h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Klasyfikacja znaków](../../c-runtime-library/character-classification.md)<br/>
[Ustawienie](../../c-runtime-library/locale.md)<br/>
[is, isw, procedury](../../c-runtime-library/is-isw-routines.md)<br/>
