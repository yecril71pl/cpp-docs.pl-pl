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
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740007"
---
# <a name="btowc"></a>btowc

Określ, czy liczba całkowita reprezentuje prawidłowy znak jednobajtowy w stanie przesunięcia początkowego.

## <a name="syntax"></a>Składnia

```C
wint_t btowc(
   int character
);
```

### <a name="parameters"></a>Parametry

*Opis*<br/>
Liczba całkowita do przetestowania.

## <a name="return-value"></a>Wartość zwracana

Zwraca reprezentację znaku dwubajtowego znak, jeśli liczba całkowita reprezentuje prawidłowy znak pojedynczej części w stanie początkowym zmiany. Zwraca WEOF, jeśli liczba całkowita to EOF lub nie jest prawidłowym znakiem jednobajtowym w stanie początkowym zmiany. Bieżące ustawienia regionalne **LC_TYPE** mają wpływ na dane wyjściowe tej funkcji.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**btowc**|\<stdio. h > lub \<WCHAR. h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
