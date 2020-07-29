---
title: rint, rintf, rintl
ms.date: 4/2/2020
api_name:
- rintf
- rintl
- rint
- _o_rint
- _o_rintf
- _o_rintl
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- rintf
- rintl
- rint
helpviewer_keywords:
- rintf function
- rint function
- rintl function
ms.assetid: 312ae3e6-278c-459a-9393-11b8f87d9184
ms.openlocfilehash: 009f56de506b50f81502a2aad7632244b069d09a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216768"
---
# <a name="rint-rintf-rintl"></a>rint, rintf, rintl

Zaokrągla wartość zmiennoprzecinkową do najbliższej liczby całkowitej w formacie liczb zmiennoprzecinkowych.

## <a name="syntax"></a>Składnia

```C
double rint( double x );
float rintf( float x );
long double rintl( long double x );
```

```cpp
float rint( float x );  // C++ only
long double rint( long double x );  // C++ only
```

### <a name="parameters"></a>Parametry

*x*<br/>
Wartość zmiennoprzecinkowa do zaokrąglenia.

## <a name="return-value"></a>Wartość zwracana

Funkcje **rukuj** zwracają wartość zmiennoprzecinkową, która reprezentuje najbliższą liczbę całkowitą do *x*. Wartości w połowie są zaokrąglane zgodnie z bieżącym ustawieniem trybu zaokrąglania zmiennoprzecinkowego, tak samo jak w przypadku funkcji **nearbyint —** . W przeciwieństwie do funkcji **nearbyint —** , funkcje **rukuj** mogą podnieść **FE_INEXACT** wyjątek zmiennoprzecinkowy, jeśli wynik różni się od argumentu. Brak powrotu błędu.

|Dane wejściowe|Wyjątek SEH|**_matherr** Oprócz|
|-----------|-------------------|--------------------------|
|± ∞, QNAN, IND|brak|brak|
|Denormalne|EXCEPTION_FLT_UNDERFLOW|brak|

## <a name="remarks"></a>Uwagi

Ponieważ C++ pozwala na Przeciążenie, można wywoływać przeciążenia **rukuj** , które pobierają i zwracają **`float`** **`long double`** wartości. W programie C **rukuj** zawsze przyjmuje i zwraca **`double`** .

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek języka C|Nagłówek C++|
|--------------|--------------|------------------|
|**rukuj**, **rintf**, **rintl**|\<math.h>|\<cmath>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_rint.c
// Build with: cl /W3 /Tc crt_rint.c
// This example displays the rounded results of
// the floating-point values 2.499999, -2.499999,
// 2.8, -2.8, 2.5 and -2.5.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 2.499999;
   float y = 2.8f;
   long double z = 2.5;

   printf("rint(%f) is %.0f\n", x, rint (x));
   printf("rint(%f) is %.0f\n", -x, rint (-x));
   printf("rintf(%f) is %.0f\n", y, rintf(y));
   printf("rintf(%f) is %.0f\n", -y, rintf(-y));
   printf("rintl(%Lf) is %.0Lf\n", z, rintl(z));
   printf("rintl(%Lf) is %.0Lf\n", -z, rintl(-z));
}
```

```Output
rint(2.499999) is 2
rint(-2.499999) is -2
rintf(2.800000) is 3
rintf(-2.800000) is -3
rintl(2.500000) is 3
rintl(-2.500000) is -3
```

## <a name="see-also"></a>Zobacz także

[Obsługa zmiennoprzecinkowa](../../c-runtime-library/floating-point-support.md)<br/>
[ceil, ceilf, ceill](ceil-ceilf-ceill.md)<br/>
[floor, floorf, floorl](floor-floorf-floorl.md)<br/>
[fmod, fmodf](fmod-fmodf.md)<br/>
[lrint, lrintf, lrintl, llrint, llrintf, llrintl](lrint-lrintf-lrintl-llrint-llrintf-llrintl.md)<br/>
[lround, lroundf, lroundl, llround, llroundf, llroundl](lround-lroundf-lroundl-llround-llroundf-llroundl.md)<br/>
[nearbyint, nearbyintf, nearbyintl](nearbyint-nearbyintf-nearbyintl1.md)<br/>
[rukuj](rint-rintf-rintl.md)<br/>
