---
title: _cabs
ms.date: 4/2/2020
api_name:
- _cabs
- _o__cabs
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: e77e1811cb6f002c06e514b5f737b8a92ea84282
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333692"
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

*Z*<br/>
Liczba zespolona.

## <a name="return-value"></a>Wartość zwracana

**_cabs** zwraca wartość bezwzględną argumentu, jeśli zakończy się pomyślnie. W przepełnieniu **_cabs** zwraca **HUGE_VAL** i ustawia **errno** na **ERANGE**. Można zmienić obsługę błędów za pomocą [_matherr](matherr.md).

## <a name="remarks"></a>Uwagi

Funkcja **_cabs** oblicza wartość bezwzględną liczby zespolonej, która musi być strukturą typu [_complex](../../c-runtime-library/standard-types.md). Struktura *z* składa się z prawdziwego składnika *x* i wyimaginowanego komponentu *y*. Wywołanie **_cabs** tworzy wartość równoważną wartości wyrażenia `sqrt( z.x * z.x + z.y * z.y )`.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_cabs**|\<> math.h|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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

[Obsługa zmiennoprzecinkowej](../../c-runtime-library/floating-point-support.md)<br/>
[abs, labs, llabs, _abs64](abs-labs-llabs-abs64.md)<br/>
[fabs, fabsf, fabsl](fabs-fabsf-fabsl.md)
