---
title: _getmaxstdio
ms.date: 11/04/2016
apiname:
- _getmaxstdio
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _getmaxstdio
- getmaxstdio
helpviewer_keywords:
- files [C++], number open
- _getmaxstdio function
- getmaxstdio function
- open files, getting number
ms.assetid: 700ca8ce-4a8c-4e00-9467-dfa9d6b831a0
ms.openlocfilehash: ea8e516b4c0806230376ea52e399c9fa1f9a858a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50618347"
---
# <a name="getmaxstdio"></a>_getmaxstdio

Zwraca liczbę jednocześnie otwartych plików, w poziomie operacje We/Wy strumienia.

## <a name="syntax"></a>Składnia

```C
int _getmaxstdio( void );
```

## <a name="return-value"></a>Wartość zwracana

Zwraca liczbę reprezentującą liczbę jednocześnie otwartych plików, które obecnie dozwolone **stdio —** poziom.

## <a name="remarks"></a>Uwagi

Użyj [_setmaxstdio —](setmaxstdio.md) Aby skonfigurować liczbę jednocześnie otwartych plików, dozwolone **stdio —** poziom.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_getmaxstdio**|\<stdio.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_setmaxstdio.c
// The program retrieves the maximum number
// of open files and prints the results
// to the console.

#include <stdio.h>

int main()
{
   printf( "%d\n", _getmaxstdio());

   _setmaxstdio(2048);

   printf( "%d\n", _getmaxstdio());
}
```

```Output
512
2048
```

## <a name="see-also"></a>Zobacz także

[Stream operacji We/Wy](../../c-runtime-library/stream-i-o.md)<br/>
