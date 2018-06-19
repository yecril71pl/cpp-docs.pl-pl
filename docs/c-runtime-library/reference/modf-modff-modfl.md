---
title: modf —, modff —, modfl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- modff
- modf
- modfl
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
- modff
- _modfl
- modf
- modfl
- math/modf
- math/modff
- math/modfl
dev_langs:
- C++
helpviewer_keywords:
- modf function
- modff function
- modfl function
ms.assetid: b1c7abf5-d476-43ca-a03c-02072a86e32d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 87cddb8b565cdc369e6b1e9679583db64039bb49
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32404834"
---
# <a name="modf-modff-modfl"></a>modf —, modff —, modfl

Dzieli wartości zmiennoprzecinkowej w ułamkowa i części liczby całkowitej.

## <a name="syntax"></a>Składnia

```C
double modf( double x, double * intptr );
float modff( float x, float * intptr );
long double modfl( long double x, long double * intptr );
```

```cpp
float modf( float x, float * intptr );  // C++ only
long double modf( long double x, long double * intptr );  // C++ only
```

### <a name="parameters"></a>Parametry

*x*<br/>
Wartość zmiennoprzecinkowa.

*IntPtr*<br/>
Wskaźnik do składowanej całkowitą część.

## <a name="return-value"></a>Wartość zwracana

Ta funkcja zwraca podpisana ułamkową część *x*. Nie ma żadnych zwracany błąd.

## <a name="remarks"></a>Uwagi

**Modf —** funkcje podzielić wartość zmiennoprzecinkową *x* do ułamkowych części i liczby całkowitej części, z których każda ma ten sam znak co *x*. Podpisana ułamkową część *x* jest zwracany. Część całkowitą są przechowywane jako wartości zmiennoprzecinkowej na *intptr*.

**modf —** ma implementację, która używa Streaming SIMD Extensions 2 (SSE2). Zobacz [_set_sse2_enable —](set-sse2-enable.md) informacje i ograniczenia dotyczące używania implementacji SSE2.

C++ pozwala przeładowanie, dlatego można wywoływać przeciążenia **modf —** który przyjmować i zwracać **float** lub **długi** **podwójne** parametrów. W programie C **modf —** zawsze ma dwie wartości double i zwraca wartość typu double.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**modf —**, **modff —**, **modfl**|C: \<math.h ><br /><br /> C++:, \<cmath > lub \<math.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_modf.c

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x, y, n;

   x = -14.87654321;      /* Divide x into its fractional */
   y = modf( x, &n );     /* and integer parts            */

   printf( "For %f, the fraction is %f and the integer is %.f\n",
           x, y, n );
}
```

```Output
For -14.876543, the fraction is -0.876543 and the integer is -14
```

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[frexp](frexp.md)<br/>
[ldexp](ldexp.md)<br/>
