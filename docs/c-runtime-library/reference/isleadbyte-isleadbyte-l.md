---
title: isleadbyte, _isleadbyte_l
ms.date: 11/04/2016
apiname:
- _isleadbyte_l
- isleadbyte
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
ms.openlocfilehash: 1a3f427e49e53bb553020da100b0e713350fab3f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62286921"
---
# <a name="isleadbyte-isleadbytel"></a>isleadbyte, _isleadbyte_l

Określa, czy znak jest wiodącym bajtem znaku wielobajtowego.

> [!IMPORTANT]
> Tego API nie można używać w aplikacjach korzystających ze środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
int isleadbyte( int c );
int _isleadbyte_l( int c );
```

### <a name="parameters"></a>Parametry

*c*<br/>
Liczba całkowita to testowania.

## <a name="return-value"></a>Wartość zwracana

**isleadbyte —** zwraca wartość różną od zera, jeśli argument spełnia warunek testu lub 0, jeśli nie jest. W ustawieniach regionalnych "języka C" i jednobajtowych (SBCS) w ustawieniach regionalnych jest zestaw znaków **isleadbyte —** zawsze zwraca wartość 0.

## <a name="remarks"></a>Uwagi

**Isleadbyte —** — makro zwraca wartość różną od zera, jeśli jej argument jest pierwszym bajtem znaku wielobajtowego. **isleadbyte —** tworzy znaczący wynik dla dowolnego całkowitego argumentu od -1 (**EOF**) do **UCHAR_MAX** (0xFF) włącznie.

Oczekiwany argument typu **isleadbyte —** jest **int**; jeśli podpisany znak jest przekazywany, kompilator może go przekonwertować na liczbę całkowitą przez rozszerzenie znaku, dając nieprzewidywalne rezultaty.

Wersja tej funkcji za pomocą **_l** sufiks jest identyczna, z tą różnicą, że używa ustawień regionalnych przekazanych w zamiast bieżących ustawień regionalnych dla swoich zachowań zależnych od ustawień regionalnych.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istleadbyte**|Zawsze zwraca wartość false|**_isleadbyte**|Zawsze zwraca wartość false|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**isleadbyte**|\<ctype.h>|
|**_isleadbyte_l**|\<ctype.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Klasyfikacja bajtów](../../c-runtime-library/byte-classification.md)<br/>
[Wersja regionalna](../../c-runtime-library/locale.md)<br/>
[_ismbb, procedury](../../c-runtime-library/ismbb-routines.md)<br/>
