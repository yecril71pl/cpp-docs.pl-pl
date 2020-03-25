---
title: _cabs
ms.date: 11/04/2016
api_name:
- _cabs
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
- api-ms-win-crt-math-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _cabs
helpviewer_keywords:
- cabs function
- absolute values
- _cabs function
- calculating absolute values
ms.assetid: fea292ee-1a39-4a0a-b416-4a189346ff26
ms.openlocfilehash: 2c2bd6b3f097095514e47b757306b4d83a990e45
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170344"
---
# <a name="_cabs"></a>_cabs

Oblicza wartość bezwzględną liczby zespolonej.

## <a name="syntax"></a>Składnia

```C
double _cabs(
   struct _complex z
);
```

### <a name="parameters"></a>Parametry

*porządku*<br/>
Liczba złożona.

## <a name="return-value"></a>Wartość zwracana

**_cabs** zwraca wartość bezwzględną argumentu, jeśli powodzenie. W przypadku przepełnienia **_cabs** zwraca **HUGE_VAL** i ustawia **errno** na **ERANGE**. Obsługę błędów można zmienić przy użyciu [_matherr](matherr.md).

## <a name="remarks"></a>Uwagi

Funkcja **_cabs** oblicza wartość bezwzględną liczby zespolonej, która musi być strukturą typu [_complex](../../c-runtime-library/standard-types.md). Struktura *z* składa się ze prawdziwego składnika *x* i części urojonej *y*. Wywołanie **_cabs** generuje wartość równoważną wartości tego wyrażenia `sqrt( z.x * z.x + z.y * z.y )`.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_cabs**|\<> Math. h|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Zobacz też

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[abs, labs, llabs, _abs64](abs-labs-llabs-abs64.md)<br/>
[fabs, fabsf, fabsl](fabs-fabsf-fabsl.md)
