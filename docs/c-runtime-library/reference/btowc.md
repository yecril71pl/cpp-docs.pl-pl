---
title: btowc
ms.date: 11/04/2016
apiname:
- btowc
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- btowc
helpviewer_keywords:
- btowc function
ms.assetid: 99a46e02-6f86-4569-af79-5feca012add8
ms.openlocfilehash: 399f56fe133a9f67ed457b435ae6c0496e1ecaa5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50514685"
---
# <a name="btowc"></a>btowc

Określanie, czy liczba całkowita reprezentuje prawidłowy znak Jednobajtowy w stanie przesunięcia początkowego.

## <a name="syntax"></a>Składnia

```C
wint_t btowc(
   int character
);
```

### <a name="parameters"></a>Parametry

*Znak*<br/>
Liczba całkowita to testowania.

## <a name="return-value"></a>Wartość zwracana

Zwraca reprezentację znaków dwubajtowych znaków, jeśli liczba całkowita reprezentuje znak Jednobajtowy prawidłowy stan przesunięcia początkowego. Zwraca WEOF, jeśli liczba całkowita jest EOF lub nie jest prawidłowy znak Jednobajtowy w stanie przesunięcia początkowego. Danymi wyjściowymi tej funkcji jest zależna od bieżącego **LC_TYPE** ustawień regionalnych.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**btowc**|\<stdio.h > lub \<wchar.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
