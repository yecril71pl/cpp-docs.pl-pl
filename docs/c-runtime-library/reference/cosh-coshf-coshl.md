---
title: COSH, coshf — coshl — | Dokumenty Microsoft
ms.custom: ''
ms.date: 04/11/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- cosh
- coshf
- coshl
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
- cosh
- coshf
- coshl
dev_langs:
- C++
helpviewer_keywords:
- cosh function
- coshf function
- coshl function
- trigonometric functions
- hyperbolic functions
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d77bb1d1b8f055bb4fe11d4c44c48fb3bf3be535
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32395474"
---
# <a name="cosh-coshf-coshl"></a>COSH coshf —, coshl —

Oblicza cosinus hiperboliczny.

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

*x*<br/>
Kąt w radianach.

## <a name="return-value"></a>Wartość zwracana

Cosinus hiperboliczny *x*.

Domyślnie, jeśli wynik jest za duża w **cosh**, **coshf —**, lub **coshl —** wywołać, funkcja zwraca **huge_val —** i ustawia **errno** do **erange —**.

|Dane wejściowe|Wyjątek SEH|Matherr — wyjątek|
|-----------|-------------------|-----------------------|
|GRANICACH **QNAN**, **IND**|brak|**_DOMAIN —**|
|*x* ≥ 7.104760e + 002|**NIEDOKŁADNY**+**PRZEPEŁNIENIEM**|**PRZEPEŁNIENIE**|

## <a name="remarks"></a>Uwagi

Ponieważ C++ pozwala przeładowanie, można wywoływać przeciążenia **cosh** który przyjmować i zwracać **float** lub **długi** **podwójne** wartości. W programie C **cosh** zawsze przyjmuje i zwraca **podwójne**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek (C)|Wymaganego nagłówka (C++)|
|-------------|---------------------|-|
|**coshf —**, **cosl —**, **coshl —**|\<math.h>|\<cmath > lub \<math.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zapoznaj się z przykładem w [sinh sinhf —, sinhl —](sinh-sinhf-sinhl.md).

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[acosh, acoshf, acoshl](acosh-acoshf-acoshl.md)<br/>
[asinh, asinhf, asinhl](asinh-asinhf-asinhl.md)<br/>
[atanh, atanhf, atanhl](atanh-atanhf-atanhl.md)<br/>
[_matherr](matherr.md)<br/>
[sinh, sinhf, sinhl](sinh-sinhf-sinhl.md)<br/>
[tanh, tanhf, tanhl](tanh-tanhf-tanhl.md)<br/>
