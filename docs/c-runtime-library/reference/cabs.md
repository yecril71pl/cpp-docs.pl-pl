---
title: _cabs
ms.date: 11/04/2016
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
helpviewer_keywords:
- cabs function
- cabsl function
- absolute values
- _cabsl function
- _cabs function
- calculating absolute values
ms.assetid: fea292ee-1a39-4a0a-b416-4a189346ff26
ms.openlocfilehash: 3e95b6f568ce66b8e9e5483bd1dcbcfaa7af3d28
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62341070"
---
# <a name="cabs"></a>_cabs

Oblicza wartość bezwzględną liczby zespolonej.

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

**_cabs** zwraca wartość bezwzględną argumentu, jeśli to się powiedzie. W przepełnieniu **_cabs** zwraca **HUGE_VAL** i ustawia **errno** do **ERANGE**. Można zmienić błąd obsługi z [_matherr](matherr.md).

## <a name="remarks"></a>Uwagi

**_Cabs** funkcja oblicza wartość bezwzględną liczby zespolonej musi być strukturą typu [_complex —](../../c-runtime-library/standard-types.md). Struktura *z* składa się z rzeczywisty składnik *x* i urojone części *y*. Wywołanie **_cabs** generuje wartość odpowiadającą wyrażenia `sqrt( z.x * z.x + z.y * z.y )`.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_cabs**|\<math.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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