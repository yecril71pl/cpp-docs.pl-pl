---
title: isleadbyte —, _isleadbyte_l — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- lead bytes
- _isleadbyte_l function
- _istleadbyte function
- istleadbyte function
- isleadbyte function
ms.assetid: 3b2bcf09-d82b-4803-9e80-59d04942802a
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dacf22d33f166527e7c464e0632366d2e39315f8
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="isleadbyte-isleadbytel"></a>isleadbyte, _isleadbyte_l

Określa, czy znak jest bajtu znaków wielobajtowych.

> [!IMPORTANT]
> Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Składnia

```C
int isleadbyte( int c );
int _isleadbyte_l( int c );
```

### <a name="parameters"></a>Parametry

*c*<br/>
Liczba całkowita do testowania.

## <a name="return-value"></a>Wartość zwracana

**isleadbyte —** zwraca wartość niezerową, jeśli argument spełnia warunek testu lub 0, jeśli jej nie ma. Zgodnie z ustawieniami regionalnymi "C" i jednobajtowych (SBCS), ustawienia regionalne, zestaw znaków **isleadbyte —** zawsze zwraca wartość 0.

## <a name="remarks"></a>Uwagi

**Isleadbyte —** makro zwraca wartość niezerową, jeśli jej argument pierwszy bajt znaków wielobajtowych. **isleadbyte —** zapewnia łatwy do rozpoznania wynik argumentu liczba całkowita od -1 (**EOF**) do **uchar_max —** (0xFF) włącznie.

Oczekiwano argumentu rodzaju **isleadbyte —** jest **int**; Jeśli podpisem znak zostanie przekazany, kompilator może ją przekonwertować na liczbę całkowitą przez rozszerzenie logowania, którego można nieprzewidywalne skutki.

Wersja tej funkcji z **_l** sufiks jest identyczny z tą różnicą, że używa ustawień regionalnych przekazana zamiast bieżące ustawienia regionalne dla jego działania zależnego od ustawień regionalnych.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istleadbyte —**|Zawsze zwraca wartość false|**_isleadbyte**|Zawsze zwraca wartość false|

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
