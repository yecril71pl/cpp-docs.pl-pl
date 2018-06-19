---
title: btowc — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- btowc function
ms.assetid: 99a46e02-6f86-4569-af79-5feca012add8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4d0e56649218e6249550638af4e198cbd1284bc2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32393319"
---
# <a name="btowc"></a>btowc

Określanie, czy liczba całkowita reprezentuje prawidłową znaków jednobajtowych w stanie początkowego przesunięcia.

## <a name="syntax"></a>Składnia

```C
wint_t btowc(
   int character
);
```

### <a name="parameters"></a>Parametry

*Znak*<br/>
Liczba całkowita do testowania.

## <a name="return-value"></a>Wartość zwracana

Zwraca reprezentację znaków dwubajtowych znaku, jeśli całkowitej reprezentuje prawidłową znaków jednobajtowych w stanie początkowego przesunięcia. Zwraca weof — Jeśli ta liczba całkowita jest EOF lub nie jest prawidłowym znakiem jednobajtowe w stanie początkowego przesunięcia. Dane wyjściowe z tej funkcji zależy od bieżącego **LC_TYPE** ustawień regionalnych.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**btowc**|\<stdio.h > lub \<wchar.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
