---
title: Drukowanie, rintf, rintl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- rintf
- rintl
- rint
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
- rintf
- rintl
- rint
dev_langs:
- C++
helpviewer_keywords:
- rintf function
- rint function
- rintl function
ms.assetid: 312ae3e6-278c-459a-9393-11b8f87d9184
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 784a540982c41ba7aa144559d3846746b59481f7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32407291"
---
# <a name="rint-rintf-rintl"></a>rint, rintf, rintl

Zaokrągla wartość zmiennoprzecinkowa do najbliższej liczby całkowitej w formacie liczb zmiennoprzecinkowych.

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
Wartość zmiennoprzecinkowa zostać zaokrąglona.

## <a name="return-value"></a>Wartość zwracana

**Drukowanie** zwracają wartość zmiennoprzecinkowa, która reprezentuje najbliższej liczby całkowitej w celu *x*. W połowie wartości są zaokrąglane zgodnie z ustawieniem bieżącego trybu zaokrąglania liczb zmiennoprzecinkowych, taka sama jak **nearbyint —** funkcji. W odróżnieniu od **nearbyint —** funkcje, **drukowanie** funkcje mogą zgłaszać **FE_INEXACT** zmiennoprzecinkowych wyjątków, jeśli wynik różni się w wartości w argumencie. Nie ma żadnych zwracany błąd.

|Dane wejściowe|Wyjątek SEH|**_matherr —** wyjątku|
|-----------|-------------------|--------------------------|
|∞; GRANICACH, QNAN, IND|brak|brak|
|Denormals|EXCEPTION_FLT_UNDERFLOW|brak|

## <a name="remarks"></a>Uwagi

Ponieważ C++ pozwala przeładowanie, można wywoływać przeciążenia **drukowanie** który przyjmować i zwracać **float** i **długi** **podwójne** wartości. W programie C **drukowanie** zawsze przyjmuje i zwraca **podwójne**.

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek C|Nagłówek C++|
|--------------|--------------|------------------|
|**Drukowanie**, **rintf**, **rintl**|\<math.h>|\<cmath >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

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

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[ceil, ceilf, ceill](ceil-ceilf-ceill.md)<br/>
[floor, floorf, floorl](floor-floorf-floorl.md)<br/>
[fmod, fmodf](fmod-fmodf.md)<br/>
[lrint, lrintf, lrintl, llrint, llrintf, llrintl](lrint-lrintf-lrintl-llrint-llrintf-llrintl.md)<br/>
[lround, lroundf, lroundl, llround, llroundf, llroundl](lround-lroundf-lroundl-llround-llroundf-llroundl.md)<br/>
[nearbyint —, nearbyintf —, nearbyintl](nearbyint-nearbyintf-nearbyintl1.md)<br/>
[rint](rint-rintf-rintl.md)<br/>