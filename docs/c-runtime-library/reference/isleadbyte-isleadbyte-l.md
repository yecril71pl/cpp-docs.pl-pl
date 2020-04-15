---
title: isleadbyte, _isleadbyte_l
ms.date: 4/2/2020
api_name:
- _isleadbyte_l
- isleadbyte
- _o__isleadbyte_l
- _o_isleadbyte
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
- _istleadbyte
- _isleadbyte_l
- isleadbyte
helpviewer_keywords:
- lead bytes
- _isleadbyte_l function
- _istleadbyte function
- istleadbyte function
- isleadbyte function
ms.assetid: 3b2bcf09-d82b-4803-9e80-59d04942802a
ms.openlocfilehash: dddf1d669f77805df8e00f506b6427603ac8fd9f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81343839"
---
# <a name="isleadbyte-_isleadbyte_l"></a>isleadbyte, _isleadbyte_l

Określa, czy znak jest bajtem wiodącym znaku wielobajtowego.

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobjęte w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
int isleadbyte( int c );
int _isleadbyte_l( int c );
```

### <a name="parameters"></a>Parametry

*C*<br/>
Całkowita ć do przetestowania.

## <a name="return-value"></a>Wartość zwracana

**isleadbyte** zwraca wartość niezerową, jeśli argument spełnia warunek testu lub 0, jeśli nie. W ustawieniach regionalnych "C" i w ustawieniach regionalnych jednobajtowych (SBCS) **isleadbyte** zawsze zwraca wartość 0.

## <a name="remarks"></a>Uwagi

Makro **isleadbyte** zwraca wartość niezerową, jeśli jego argument jest pierwszym bajtem znaku wielobajtowego. **isleadbyte** daje znaczący wynik dla dowolnego argumentu liczby całkowitej od -1 **(EOF**) do **UCHAR_MAX** (0xFF), włącznie.

Oczekiwany typ argumentu **isleadbyte** jest **int**; Jeśli podpisany znak jest przekazywany, kompilator może przekonwertować go na całkowitą przez rozszerzenie znaku, dając nieprzewidywalne wyniki.

Wersja tej funkcji z sufiksem **_l** jest identyczna, z tą różnicą, że używa ustawień regionalnych przekazanych zamiast bieżących ustawień regionalnych dla zachowania zależnego od ustawień regionalnych.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE nie zdefiniowano & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istleadbyte**|Zawsze zwraca fałsz|**_isleadbyte**|Zawsze zwraca fałsz|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**isleadbyte**|\<ctype.h>|
|**_isleadbyte_l**|\<ctype.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Klasyfikacja bajtów](../../c-runtime-library/byte-classification.md)<br/>
[Ustawienia regionalne](../../c-runtime-library/locale.md)<br/>
[_ismbb, procedury](../../c-runtime-library/ismbb-routines.md)<br/>
