---
title: scalbn, scalbnf, scalbnl, scalbln, scalblnf, scalblnl
description: Dokumentacja interfejsu API dla scalbn —, scalbnf —, scalbnl, scalbln, scalblnf i scalblnl; który mnoży liczbę zmiennoprzecinkową przez integralną moc `FLT_RADIX` .
ms.date: 9/1/2020
api_name:
- scalblnl
- scalbnl
- scalbnf
- scalblnf
- scalbn
- scalbln
- _o_scalbln
- _o_scalblnf
- _o_scalblnl
- _o_scalbn
- _o_scalbnf
- _o_scalbnl
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
- scalblnf
- scalbnl
- scalblnl
- scalbln
- scalbn
- scalbnf
helpviewer_keywords:
- scalbn function
- scalbln function
- scalblnl function
- scalbnl function
- scalbnf function
- scalblnf function
ms.assetid: df2f1543-8e39-4af4-a5cf-29307e64807d
ms.openlocfilehash: 1a01811e5fcfb28c0557e0232d76649c867748b1
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556674"
---
# <a name="scalbn-scalbnf-scalbnl-scalbln-scalblnf-scalblnl"></a>scalbn, scalbnf, scalbnl, scalbln, scalblnf, scalblnl

Mnoży liczbę zmiennoprzecinkową przez integralną moc FLT_RADIX.

## <a name="syntax"></a>Składnia

```C
double scalbn(
   double x,
   int exp
);
float scalbn(
   float x,
   int exp
);  // C++ only
long double scalbn(
   long double x,
   int exp
);  // C++ only
float scalbnf(
   float x,
   int exp
);
long double scalbnl(
   long double x,
   int exp
);

#define scalbn(X, INT) // Requires C11 or higher

double scalbln(
   double x,
   long exp
);

float scalblnf(
   float x,
   long exp
);
long double scalblnl(
   long double x,
   long exp
);

#define scalbln(X, LONG) // Requires C11 or higher

float scalbln(
   float x,
   long exp
);  // C++ only
long double scalbln(
   long double x,
   long exp
);  // C++ only
```

### <a name="parameters"></a>Parametry

*y*\
Wartość zmiennoprzecinkowa.

*EXP*\
Wykładnik wartości całkowitej.

## <a name="return-value"></a>Wartość zwracana

Funkcja **scalbn —** zwraca wartość *x* \* **FLT_RADIX**<sup>EXP</sup> po pomyślnym wykonaniu. W przypadku przepełnienia (w zależności od znaku *x*) **scalbn —** zwraca +/- **HUGE_VAL**; wartość **errno** jest ustawiona na **ERANGE**.

Aby uzyskać więcej informacji na temat **errno** i możliwych zwracanych wartości błędów, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**FLT_RADIX** jest zdefiniowany \<float.h> jako natywny zmiennoprzecinkowy podstawy; w systemach binarnych ma wartość 2, a **scalbn —** jest odpowiednikiem [ldexp —](ldexp.md).

Ponieważ C++ pozwala na Przeciążenie, można wywoływać przeciążenia **scalbn —** i **scalbln** , które pobierają i zwracają **`float`** lub **`long double`** typu. W programie C, chyba że używasz \<tgmath.h> makra do wywołania tej funkcji, **scalbn —** zawsze przyjmuje i i zwraca i **`double`** **`int`** **`double`** , a **scalbln** zawsze przyjmuje a i **`double`** **`long`** zwraca **`double`** .

Jeśli używasz \<tgmath.h> `scalbn()` `scalbln` makra lub, typ argumentu określa, która wersja funkcji jest wybrana. Aby uzyskać szczegółowe informacje, zobacz [matematyka typu ogólnego](../../c-runtime-library/tgmath.md) .

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek języka C|Nagłówek C++|
|--------------|--------------|------------------|
|**scalbn —**, **scalbnf —**, **scalbnl**, **scalbln**, **scalblnf**, **scalblnl**|\<math.h>|\<cmath>|
|**scalbn — () lub scalbln** — makro | \<tgmath.h> ||

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_scalbn.c
// Compile using: cl /W4 crt_scalbn.c
#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 6.4, y;
   int p = 3;

   y = scalbn( x, p );
   printf( "%2.1f times FLT_RADIX to the power of %d is %2.1f\n", x, p, y );
}
```

### <a name="output"></a>Dane wyjściowe

```Output
6.4 times FLT_RADIX to the power of 3 is 51.2
```

## <a name="see-also"></a>Zobacz też

[Obsługa zmiennoprzecinkowa](../../c-runtime-library/floating-point-support.md)<br/>
[frexp](frexp.md)<br/>
[ldexp](ldexp.md)<br/>
[modf, modff, modfl](modf-modff-modfl.md)<br/>
