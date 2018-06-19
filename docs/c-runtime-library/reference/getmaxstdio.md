---
title: _getmaxstdio | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- files [C++], number open
- _getmaxstdio function
- getmaxstdio function
- open files, getting number
ms.assetid: 700ca8ce-4a8c-4e00-9467-dfa9d6b831a0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f2030937806eedbf1abe671032da75c531fdd5ca
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32396787"
---
# <a name="getmaxstdio"></a>_getmaxstdio

Zwraca liczbę równocześnie otwarte pliki w poziomie we/wy strumienia.

## <a name="syntax"></a>Składnia

```C
int _getmaxstdio( void );
```

## <a name="return-value"></a>Wartość zwracana

Zwraca liczbę reprezentującą liczbę jednocześnie otwartych plików, w obecnie dozwolone **stdio —** poziom.

## <a name="remarks"></a>Uwagi

Użyj [_setmaxstdio —](setmaxstdio.md) Aby skonfigurować liczbę równocześnie otwarte pliki w **stdio —** poziom.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_getmaxstdio**|\<stdio.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
