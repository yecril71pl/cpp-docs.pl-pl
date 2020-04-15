---
title: scalbn, scalbnf, scalbnl, scalbln, scalblnf, scalblnl
ms.date: 4/2/2020
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: d0c7f6db7ad6970be85203eef76e5ccb152e2200
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332600"
---
# <a name="scalbn-scalbnf-scalbnl-scalbln-scalblnf-scalblnl"></a>scalbn, scalbnf, scalbnl, scalbln, scalblnf, scalblnl

Mnoży liczbę zmiennoprzecinkowe przez integralną moc FLT_RADIX.

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
double scalbln(
   double x,
   long exp
);
float scalbln(
   float x,
   long exp
);  // C++ only
long double scalbln(
   long double x,
   long exp
);  // C++ only
float scalblnf(
   float x,
   long exp
);
long double scalblnl(
   long double x,
   long exp
);
```

### <a name="parameters"></a>Parametry

*X*<br/>
Wartość zmiennoprzecinku.

*Exp*<br/>
Wykładnik liczby całkowitej.

## <a name="return-value"></a>Wartość zwracana

Funkcje **scalbn** zwracają wartość *x* \* **FLT_RADIX**<sup>exp</sup> po pomyślnym. Przy przepełnienie (w zależności od znaku *x),* **scalbn** zwraca +/- **HUGE_VAL**; wartość **errno** jest ustawiona na **ERANGE**.

Aby uzyskać więcej informacji na temat **errno** i możliwych wartości zwracania błędów, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**FLT_RADIX** jest zdefiniowany \<w> float.h jako natywny radix zmiennoprzecinkowy; w systemach binarnych, ma wartość 2, a **scalbn** jest odpowiednikiem [ldexp](ldexp.md).

Ponieważ C++ umożliwia przeciążenie, można wywołać przeciążenia **scalbn** i **scalbln,** które biorą i zwracają **float** lub **długie** **podwójne** typy. W programie C, **scalbn** zawsze ma **podwójne** i **int** i zwraca **podwójne**, i **scalbln** zawsze ma **podwójne** i **długie** i zwraca **podwójne**.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek C|Nagłówek języka C++|
|--------------|--------------|------------------|
|**scalbn**, **scalbnf**, **scalbnl**, **scalbln**, **scalblnf**, **scalblnl**|\<> math.h|\<> cmath|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

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

[Obsługa zmiennoprzecinkowej](../../c-runtime-library/floating-point-support.md)<br/>
[frexp](frexp.md)<br/>
[ldexp](ldexp.md)<br/>
[modf, modff, modfl](modf-modff-modfl.md)<br/>
