---
title: _cabs — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _cabs
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
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- cabsl
- _cabs
- _cabsl
dev_langs:
- C++
helpviewer_keywords:
- cabs function
- cabsl function
- absolute values
- _cabsl function
- _cabs function
- calculating absolute values
ms.assetid: fea292ee-1a39-4a0a-b416-4a189346ff26
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 345130fe72b7dd1ee416209c5702d877a036561c
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="cabs"></a>_cabs

Oblicza wartość bezwzględną liczby złożonej.

## <a name="syntax"></a>Składnia

```C
double _cabs(
   struct _complex z
);
```

### <a name="parameters"></a>Parametry

*z*<br/>
Liczba złożonych.

## <a name="return-value"></a>Wartość zwracana

**_cabs —** zwraca wartość bezwzględną liczby argumentu, w przypadku powodzenia. Na przepełnienia **_cabs —** zwraca **huge_val —** i ustawia **errno** do **erange —**. Można zmienić błąd obsługi z [_matherr —](matherr.md).

## <a name="remarks"></a>Uwagi

**_Cabs —** funkcja oblicza wartość bezwzględna liczby złożonej, który musi być struktura typu [_complex](../../c-runtime-library/standard-types.md). Struktura *z* składa się z rzeczywistą składnika *x* i składnika urojony *y*. Wywołanie **_cabs —** daje wartość odpowiadającą wyrażenie `sqrt( z.x * z.x + z.y * z.y )`.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_cabs**|\<math.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_cabs.c
// Using _cabs, this program calculates
// the absolute value of a complex number.

#include <math.h>
#include <stdio.h>

int main( void )
{
   struct _complex number = { 3.0, 4.0 };
   double d;

   d = _cabs( number );
   printf( "The absolute value of %f + %fi is %f\n",
           number.x, number.y, d );
}
```

```Output
The absolute value of 3.000000 + 4.000000i is 5.000000
```

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[abs, labs, llabs, _abs64](abs-labs-llabs-abs64.md)<br/>
[fabs, fabsf, fabsl](fabs-fabsf-fabsl.md)   