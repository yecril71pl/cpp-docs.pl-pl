---
title: lround, lroundf, lroundl, llround, llroundf, llroundl
description: Dokumentacja interfejsu API dla lround, lroundf, lroundl, llround, llroundf i llroundl; który Zaokrągla wartość zmiennoprzecinkową do najbliższej liczby całkowitej.
ms.date: 9/1/2020
api_name:
- llround
- llroundf
- llroundl
- lroundf
- lround
- lroundl
- _o_llround
- _o_llroundf
- _o_llroundl
- _o_lround
- _o_lroundf
- _o_lroundl
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
- lround
- lroundl
- llroundl
- llround
- lroundf
- llroundf
helpviewer_keywords:
- lround function
- llroundl function
- llround function
- lroundf function
- llroundf function
- lroundl function
ms.assetid: cfb88a35-54c6-469f-85af-f7d695dcfdd8
ms.openlocfilehash: c5db62da7cdba58fdc58e8acbfe3aff0e2c386d6
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555322"
---
# <a name="lround-lroundf-lroundl-llround-llroundf-llroundl"></a>lround, lroundf, lroundl, llround, llroundf, llroundl

Zaokrągla wartość zmiennoprzecinkową do najbliższej liczby całkowitej.

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
#define lround(X) // Requires C11 or higher
```

### <a name="parameters"></a>Parametry

*y*\
Wartość zmiennoprzecinkowa do zaokrąglenia.

## <a name="return-value"></a>Wartość zwracana

Funkcje **lround** i **llround** zwracają najbliższą **`long`** lub **`long long`** całkowitą liczbę do *x*. Połowy wartości są zaokrąglane w kierunku od zera, niezależnie od ustawienia trybu zaokrąglania zmiennoprzecinkowego. Nie ma żadnego powrotu błędu.

|Dane wejściowe|Wyjątek SEH|Wyjątek Matherr|
|-----------|-------------------|-----------------------|
|**QNAN**, **IND**|brak|**_DOMAIN**|

## <a name="remarks"></a>Uwagi

Ponieważ C++ pozwala na Przeciążenie, można wywoływać przeciążenia **lround** lub **llround** , które pobierają i zwracają **`float`** **`long double`** wartości. W programie C, jeśli nie używasz \<tgmath.h> makra do wywołania tej funkcji, **lround** i **llround** zawsze przyjmują i zwracają **`double`** .

Jeśli używasz \<tgmath.h> `lround()` makra, typ argumentu określa, która wersja funkcji jest wybrana. Aby uzyskać szczegółowe informacje, zobacz [matematyka typu ogólnego](../../c-runtime-library/tgmath.md) .

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**lround**, **lroundf**, **lroundl**, **llround**, **llroundf**, **llroundl**|\<math.h>|
|**lround** — makro | \<tgmath.h> ||

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_lround.c
// Build with: cl /W4 /Tc crt_lround.c
// This example displays the rounded results of
// the floating-point values 2.499999, -2.499999,
// 2.8, -2.8, 3.5 and -3.5.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 2.499999;
   float y = 2.8f;
   long double z = 3.5L;

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
lroundl(3.500000) is 4
lroundl(-3.500000) is -4
```

## <a name="see-also"></a>Zobacz też

[Obsługa zmiennoprzecinkowa](../../c-runtime-library/floating-point-support.md)<br/>
[ceil, ceilf, ceill](ceil-ceilf-ceill.md)<br/>
[floor, floorf, floorl](floor-floorf-floorl.md)<br/>
[fmod, fmodf](fmod-fmodf.md)<br/>
[lrint, lrintf, lrintl, llrint, llrintf, llrintl](lrint-lrintf-lrintl-llrint-llrintf-llrintl.md)<br/>
[round, roundf, roundl](round-roundf-roundl.md)<br/>
[nearbyint, nearbyintf, nearbyintl](nearbyint-nearbyintf-nearbyintl1.md)<br/>
[rint, rintf, rintl](rint-rintf-rintl.md)<br/>
