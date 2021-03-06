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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 1d2202bd1ca59ee42287c398da429df132e24fcb
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234084"
---
# <a name="isleadbyte-_isleadbyte_l"></a>isleadbyte, _isleadbyte_l

Określa, czy znak jest bajtem wiodącym znaku wielobajtowego.

> [!IMPORTANT]
> Tego interfejsu API nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platforma uniwersalna systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
int isleadbyte( int c );
int _isleadbyte_l( int c );
```

### <a name="parameters"></a>Parametry

*s*<br/>
Liczba całkowita do przetestowania.

## <a name="return-value"></a>Wartość zwracana

**isleadbyte** zwraca wartość różną od zera, jeśli argument spełnia warunek testu lub 0, jeśli tak nie jest. W ustawieniach regionalnych "C" i w zestawie znaków jednobajtowych (SBCS) **isleadbyte** zawsze zwraca 0.

## <a name="remarks"></a>Uwagi

Makro **isleadbyte** zwraca wartość różną od zera, jeśli jej argument jest pierwszym bajtem znaku wielobajtowego. **isleadbyte** generuje znaczący wynik dla dowolnego argumentu całkowitego z-1 (**EOF**) do **UCHAR_MAX** (0xFF), włącznie.

Oczekiwanym typem argumentu **isleadbyte** jest **`int`** ; Jeśli zostanie przesłany znak podpisany, kompilator może przekonwertować go na liczbę całkowitą za pomocą rozszerzenia znaku, co daje nieprzewidywalne wyniki.

Wersja tej funkcji z sufiksem **_l** jest identyczna, z tą różnicą, że używa przeszukanych ustawień regionalnych zamiast bieżących ustawień regionalnych dla zachowań zależnych od ustawień regionalnych.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _MBCS _UNICODE &|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istleadbyte**|Zawsze zwraca wartość false|**_isleadbyte**|Zawsze zwraca wartość false|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**isleadbyte**|\<ctype.h>|
|**_isleadbyte_l**|\<ctype.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Klasyfikacja bajtów](../../c-runtime-library/byte-classification.md)<br/>
[Regionalne](../../c-runtime-library/locale.md)<br/>
[Procedury _ismbb](../../c-runtime-library/ismbb-routines.md)<br/>
