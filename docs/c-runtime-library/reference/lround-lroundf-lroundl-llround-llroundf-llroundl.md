---
title: lround —, lroundf —, lroundl —, llround —, llroundf —, llroundl — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- llround
- llroundf
- llroundl
- lroundf
- lround
- lroundl
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
- lround
- lroundl
- llroundl
- llround
- lroundf
- llroundf
dev_langs:
- C++
helpviewer_keywords:
- lround function
- llroundl function
- llround function
- lroundf function
- llroundf function
- lroundl function
ms.assetid: cfb88a35-54c6-469f-85af-f7d695dcfdd8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d9af035e65e383c8027c8c19df02e18c298f625e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32401051"
---
# <a name="lround-lroundf-lroundl-llround-llroundf-llroundl"></a>lround, lroundf, lroundl, llround, llroundf, llroundl

Zaokrągla wartość zmiennoprzecinkowa do najbliższej liczby całkowitej.

## <a name="syntax"></a>Składnia

```C
long lround(
   double x
);
long lround(
   float x
);  // C++ only
long lround(
   long double x
);  // C++ only
long lroundf(
   float x
);
long lroundl(
   long double x
);
long long llround(
   double x
);
long long llround(
   float x
);  // C++ only
long long llround(
   long double x
);  // C++ only
long long llroundf(
   float x
);
long long llroundl(
   long double x
);
```

### <a name="parameters"></a>Parametry

*x*<br/>
Wartość zmiennoprzecinkowa zostać zaokrąglona.

## <a name="return-value"></a>Wartość zwracana

**Lround —** i **llround —** zwracają najbliższej **długi** lub **długi** **długi** liczba całkowita *x*. W połowie wartości są zaokrąglane w kierunku od zera, bez względu na ustawienie trybu zaokrąglania liczb zmiennoprzecinkowych. Nie ma żadnych zwracany błąd.

|Dane wejściowe|Wyjątek SEH|Matherr — wyjątek|
|-----------|-------------------|-----------------------|
|GRANICACH **QNAN**, **IND**|brak|**_DOMAIN —**|

## <a name="remarks"></a>Uwagi

Ponieważ C++ pozwala przeładowanie, można wywoływać przeciążenia **lround —** lub **llround —** który przyjmować i zwracać **float** i **długi** **podwójne** wartości. W programie C **lround —** i **llround —** zawsze przyjmować i zwracać **podwójne**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**lround —**, **lroundf —**, **lroundl —**, **llround —**, **llroundf —**, **llroundl —**|\<math.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_lround.c
// Build with: cl /W3 /Tc crt_lround.c
// This example displays the rounded results of
// the floating-point values 2.499999, -2.499999,
// 2.8, -2.8, 3.5 and -3.5.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 2.499999;
   float y = 2.8f;
   long double z = 3.5;

   printf("lround(%f) is %d\n", x, lround(x));
   printf("lround(%f) is %d\n", -x, lround(-x));
   printf("lroundf(%f) is %d\n", y, lroundf(y));
   printf("lroundf(%f) is %d\n", -y, lroundf(-y));
   printf("lroundl(%Lf) is %d\n", z, lroundl(z));
   printf("lroundl(%Lf) is %d\n", -z, lroundl(-z));
}
```

```Output
lround(2.499999) is 2
lround(-2.499999) is -2
lroundf(2.800000) is 3
lroundf(-2.800000) is -3
lroundl(2.500000) is 4
lroundl(-2.500000) is -4
```

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[ceil, ceilf, ceill](ceil-ceilf-ceill.md)<br/>
[floor, floorf, floorl](floor-floorf-floorl.md)<br/>
[fmod, fmodf](fmod-fmodf.md)<br/>
[lrint, lrintf, lrintl, llrint, llrintf, llrintl](lrint-lrintf-lrintl-llrint-llrintf-llrintl.md)<br/>
[round, roundf, roundl](round-roundf-roundl.md)<br/>
[nearbyint —, nearbyintf —, nearbyintl](nearbyint-nearbyintf-nearbyintl1.md)<br/>
[rint, rintf, rintl](rint-rintf-rintl.md)<br/>
