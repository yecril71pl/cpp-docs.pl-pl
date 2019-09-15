---
title: btowc
ms.date: 11/04/2016
api_name:
- btowc
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
- api-ms-win-crt-convert-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- btowc
helpviewer_keywords:
- btowc function
ms.assetid: 99a46e02-6f86-4569-af79-5feca012add8
ms.openlocfilehash: 1f03fce8686f919af85ee3751cb9a0a3fca1ede7
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70943466"
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
