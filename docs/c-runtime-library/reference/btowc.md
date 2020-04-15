---
title: btowc
ms.date: 4/2/2020
api_name:
- btowc
- _o_btowc
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- btowc
helpviewer_keywords:
- btowc function
ms.assetid: 99a46e02-6f86-4569-af79-5feca012add8
ms.openlocfilehash: b4262f31c95b5272e3917f58a6c945577d401f16
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333760"
---
# <a name="btowc"></a>btowc

Określ, czy liczba całkowita reprezentuje prawidłowy znak jedno bajtowy w początkowym stanie przesunięcia.

## <a name="syntax"></a>Składnia

```C
wint_t btowc(
   int character
);
```

### <a name="parameters"></a>Parametry

*Znaków*<br/>
Całkowita ć do przetestowania.

## <a name="return-value"></a>Wartość zwracana

Zwraca reprezentację znaku z szerokimi znakami, jeśli liczba całkowita reprezentuje prawidłowy znak jedno bajtowy w początkowym stanie przesunięcia. Zwraca weof, jeśli liczba całkowita jest EOF lub nie jest prawidłowym znakiem jedno bajtowym w początkowym stanie przesunięcia. Dane wyjściowe tej funkcji ma wpływ bieżącej **LC_TYPE** ustawień regionalnych.

## <a name="remarks"></a>Uwagi

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**btowc**|\<stdio.h> lub \<wchar.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
