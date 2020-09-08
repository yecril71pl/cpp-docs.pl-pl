---
title: sqrt, sqrtf, sqrtl
description: Dokumentacja interfejsu API dla funkcji sqrt, sqrtf — i sqrt; które oblicza pierwiastek kwadratowy liczby zmiennoprzecinkowej.
ms.date: 08/31/2020
api_name:
- sqrtl
- sqrtf
- sqrt
- _o_sqrt
- _o_sqrtf
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
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- sqrt
- sqrtf
- _sqrtl
helpviewer_keywords:
- sqrtf function
- sqrt function
- sqrtl function
- _sqrtl function
- calculating square roots
- square roots, calculating
ms.assetid: 2ba9467b-f172-41dc-8f10-b86f68fa813c
ms.openlocfilehash: 17526b4e4a7eca5d36c01069dbe975bb035d1f58
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556778"
---
# <a name="sqrt-sqrtf-sqrtl"></a>sqrt, sqrtf, sqrtl

Oblicza pierwiastek kwadratowy.

## <a name="syntax"></a>Składnia

```C
double sqrt(
   double x
);
float sqrt(
   float x
);  // C++ only
long double sqrt(
   long double x
);  // C++ only
float sqrtf(
   float x
);
long double sqrtl(
   long double x
);
#define sqrt(x) // Requires C11 or higher
```

### <a name="parameters"></a>Parametry

*y*\
Nieujemna wartość zmiennoprzecinkowa

## <a name="remarks"></a>Uwagi

Ponieważ C++ pozwala na Przeciążenie, można wywoływać przeciążenia klasy **sqrt** przyjmującej **`float`** lub **`long double`** typu. W programie C, jeśli nie używasz \<tgmath.h> makra do wywołania tej funkcji, **sqrt** zawsze przyjmuje i zwraca **`double`** .

Jeśli używasz \<tgmath.h> `sqrt()` makra, typ argumentu określa, która wersja funkcji jest wybrana. Aby uzyskać szczegółowe informacje, zobacz [matematyka typu ogólnego](../../c-runtime-library/tgmath.md) .

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="return-value"></a>Wartość zwracana

Funkcje **sqrt** zwracają pierwiastek kwadratowy wartości *x*. Domyślnie, jeśli *x* jest ujemna, **sqrt** zwraca nieokreślony NaN.

|Dane wejściowe|Wyjątek SEH|**_matherr** Oprócz|
|-----------|-------------------|--------------------------|
|QNAN, IND|brak|_DOMAIN|
|- ∞|brak|_DOMAIN|
|x<0|brak|_DOMAIN|

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek języka C|Nagłówek C++|
|--------------|--------------|------------------|
|**sqrt**, **sqrtf —**, **sqrt**|\<math.h>|\<cmath>|
|**sqrt ()** — makro | \<tgmath.h> ||

Aby uzyskać informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_sqrt.c
// This program calculates a square root.

#include <math.h>
#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   double question = 45.35, answer;
   answer = sqrt( question );
   if( question < 0 )
      printf( "Error: sqrt returns %f\n", answer );
   else
      printf( "The square root of %.2f is %.2f\n", question, answer );
}
```

```Output
The square root of 45.35 is 6.73
```

## <a name="see-also"></a>Zobacz też

[Obsługa zmiennoprzecinkowa](../../c-runtime-library/floating-point-support.md)<br/>
[exp, expf, expl](exp-expf.md)<br/>
[log, logf, log10, log10f](log-logf-log10-log10f.md)<br/>
[pow, powf, powl](pow-powf-powl.md)<br/>
[_CIsqrt](../../c-runtime-library/cisqrt.md)<br/>
