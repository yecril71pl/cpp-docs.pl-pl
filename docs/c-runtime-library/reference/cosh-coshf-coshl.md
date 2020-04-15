---
title: cosh, coshf, coshl
ms.date: 4/2/2020
api_name:
- cosh
- coshf
- coshl
- _o_cosh
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
- cosh
- coshf
- coshl
helpviewer_keywords:
- cosh function
- coshf function
- coshl function
- trigonometric functions
- hyperbolic functions
ms.openlocfilehash: d7d2050be406e7f2be66ca200d1e3cfd9c2960b0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348444"
---
# <a name="cosh-coshf-coshl"></a>cosh, coshf, coshl

Oblicza cosine hiperboliczne.

## <a name="syntax"></a>Składnia

```C
double cosh( double x );
float coshf( float x );
long double coshl( long double x );
```

```cpp
float cosh( float x );  // C++ only
long double cosh( long double x );  // C++ only
```

### <a name="parameters"></a>Parametry

*X*<br/>
Kąt w radianach.

## <a name="return-value"></a>Wartość zwracana

Cosine hiperboliczny *x*.

Domyślnie, jeśli wynik jest zbyt duży w **wywołaniu cosh**, **coshf**lub **coshl,** funkcja zwraca **HUGE_VAL** i ustawia **errno** na **ERANGE**.

|Dane wejściowe|Wyjątek SEH|Wyjątek Matherr|
|-----------|-------------------|-----------------------|
|± **QNAN**, **IND**|brak|**_DOMAIN**|
|*x* ≥ 7,104760e+002|**NIEDOKŁADNE**+**PRZEPEŁNIENIE**|**Przepełnienie**|

## <a name="remarks"></a>Uwagi

Ponieważ C++ umożliwia przeciążenie, można wywołać przeciążenia **cosh,** które biorą i zwracają **float** lub **długie** **podwójne** wartości. W programie C **cosh** zawsze przyjmuje i zwraca **podwójny**plik .

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek (C)|Wymagany nagłówek (C++)|
|-------------|---------------------|-|
|**coshf**, **cosl**, **coshl**|\<> math.h|\<cmath> lub \<math.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład w [sinh, sinhf, sinhl](sinh-sinhf-sinhl.md).

## <a name="see-also"></a>Zobacz też

[Obsługa zmiennoprzecinkowej](../../c-runtime-library/floating-point-support.md)<br/>
[acosh, acoshf, acoshl](acosh-acoshf-acoshl.md)<br/>
[asinh, asinhf, asinhl](asinh-asinhf-asinhl.md)<br/>
[atanh, atanhf, atanhl](atanh-atanhf-atanhl.md)<br/>
[_matherr](matherr.md)<br/>
[sinh, sinhf, sinhl](sinh-sinhf-sinhl.md)<br/>
[tanh, tanhf, tanhl](tanh-tanhf-tanhl.md)<br/>
