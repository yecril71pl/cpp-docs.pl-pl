---
title: isblank, iswblank, _isblank_l, _iswblank_l
ms.date: 4/2/2020
api_name:
- isblank
- _isblank_l
- iswblank
- _iswblank_l
- _o_isblank
- _o_iswblank
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
- _iswblank_l
- isblank
- _istblank_l
- _istblank
- _isblank_l
- iswblank
ms.assetid: 33ce96c0-f387-411a-8283-c3d2a69e56bd
ms.openlocfilehash: 736a0791f1e5ee4b11e61164861cc6dc0c7a9c87
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81343891"
---
# <a name="isblank-iswblank-_isblank_l-_iswblank_l"></a>isblank, iswblank, _isblank_l, _iswblank_l

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

*C*<br/>
Całkowita ć do przetestowania.

*Ustawień regionalnych*<br/>
Ustawienia regionalne do użycia.

## <a name="return-value"></a>Wartość zwracana

Każda z tych procedur zwraca wartość niezerową, jeśli *c* jest określoną reprezentacją spacji lub poziomego znaku karty lub jest jednym z zestawu znaków specyficznych dla ustawień regionalnych, które są używane do oddzielania wyrazów w wierszu tekstu. **isblank** zwraca wartość niezerową, jeśli *c* jest znakiem spacji (0x20) lub znakiem zakładki poziomej (0x09). Wynik stanu badania dla funkcji **isblank** zależy od **LC_CTYPE** ustawienie kategorii ustawień regionalnych; aby uzyskać więcej informacji, zobacz [setlocale, _wsetlocale](setlocale-wsetlocale.md). Wersje tych funkcji, które nie mają sufiksu **_l,** używają bieżących ustawień regionalnych dla zachowania zależnego od ustawień regionalnych; wersje, które mają **_l** sufiks są identyczne, z tą różnicą, że używają ustawień regionalnych, które są przekazywane zamiast. Aby uzyskać więcej informacji, zobacz [Ustawienia regionalne](../../c-runtime-library/locale.md).

**iswblank** zwraca wartość różną od zera, jeśli *c* jest szerokim znakiem odpowiadającym standardowemu spacji lub poziomemu znakowi karty.

Zachowanie **isblank** i **_isblank_l** jest niezdefiniowana, jeśli *c* nie jest EOF lub w zakresie od 0 do 0xFF włącznie. Gdy biblioteka CRT debugowania jest używana i *c* nie jest jedną z tych wartości, funkcje podnieść potwierdzenia.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istblank**|**isblank**|[_ismbcblank](ismbcgraph-functions.md)|**iswblank (iswblank)**|
|**_istblank_l**|**_isblank_l**|[_ismbcblank_l](ismbcgraph-functions.md)|**_iswblank_l**|

## <a name="remarks"></a>Uwagi

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**isblank**|\<ctype.h>|
|**iswblank (iswblank)**|\<ctype.h> lub \<wchar.h>|
|**_isblank_l**|\<ctype.h>|
|**_iswblank_l**|\<ctype.h> lub \<wchar.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Klasyfikacja znaków](../../c-runtime-library/character-classification.md)<br/>
[Ustawienia regionalne](../../c-runtime-library/locale.md)<br/>
[is, isw, procedury](../../c-runtime-library/is-isw-routines.md)<br/>
