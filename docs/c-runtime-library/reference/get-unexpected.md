---
title: _get_unexpected
ms.date: 11/04/2016
apiname:
- _get_unexpected
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
apitype: DLLExport
f1_keywords:
- __get_unexpected
- _get_unexpected
- get_unexpected
helpviewer_keywords:
- __get_unexpected function
- get_unexpected function
- _get_unexpected function
ms.assetid: a5f7a7a0-18e0-485e-953d-db291068a1e8
ms.openlocfilehash: 225158ecab60a5997ebedbad107eb43d82189234
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50519408"
---
# <a name="getunexpected"></a>_get_unexpected

Zwraca procedury zakończenia, który ma zostać wywołana przez **nieoczekiwany**.

## <a name="syntax"></a>Składnia

```C
unexpected_function _get_unexpected( void );
```

## <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do funkcji zarejestrowane przez [set_unexpected](set-unexpected-crt.md). Jeśli żadna funkcja nie została ustawiona, wartość zwracana mogą służyć do przywracania domyślne zachowanie; Ta wartość może być **NULL**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_get_unexpected**|\<eh.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Obsługa wyjątków — procedury](../../c-runtime-library/exception-handling-routines.md)<br/>
[abort](abort.md)<br/>
[set_terminate](set-terminate-crt.md)<br/>
[Zakończenie](terminate-crt.md)<br/>
[Nieoczekiwany](unexpected-crt.md)<br/>
