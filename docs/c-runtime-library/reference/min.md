---
title: __min — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- __min
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
- __min
- min
- _min
dev_langs:
- C++
helpviewer_keywords:
- __min macro
- min macro
- minimum macro
- _min macro
ms.assetid: 2037f26c-b48a-4a69-8870-22519f052a3c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0cc69cb018cda6fc093c570dab86a8df4cf396b7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32399611"
---
# <a name="min"></a>__min

Makro preprocesora, które zwraca mniejszy z dwóch wartości.

## <a name="syntax"></a>Składnia

```C
#define __min(a,b) (((a) < (b)) ? (a) : (b))
```

### <a name="parameters"></a>Parametry

*a*, *b*<br/>
Typ wartości dowolnego, które **<** operator działa na.

## <a name="return-value"></a>Wartość zwracana

Mniejszy z dwóch argumentów.

## <a name="remarks"></a>Uwagi

**__Min —** makro porównuje dwie wartości i zwraca wartość mniejszy. Argumenty mogą być dowolnego liczbowego typu danych, podpisu lub bez znaku. Zarówno argumentów i zwracana wartość musi być tego samego typu danych.

Argument zwrócił jest oceniane dwukrotnie przez makra. Może to prowadzić do nieoczekiwanych wyników, jeśli wartością argumentu jest wyrażenie, które zmienia jego wartość, gdy wartość jest szacowana, takich jak `*p++`.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**__min**|\<stdlib.h>|

## <a name="example"></a>Przykład

```C
// crt_minmax.c

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   int a = 10;
   int b = 21;

   printf( "The larger of %d and %d is %d\n",  a, b, __max( a, b ) );
   printf( "The smaller of %d and %d is %d\n", a, b, __min( a, b ) );
}
```

```Output
The larger of 10 and 21 is 21
The smaller of 10 and 21 is 10
```

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[__max](max.md)<br/>
