---
title: asin, asinf, asinl
ms.date: 04/05/2018
api_name:
- asinf
- asinl
- asin
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- asin
- asinl
- asinf
helpviewer_keywords:
- asin function
- asinl function
- asinf function
- trigonometric functions
- arcsine function
ms.assetid: ca05f9ea-b711-49f6-9f32-2f4019abfd69
ms.openlocfilehash: 1e70c9b2187b97d3dea589c1757081da8bf2bd10
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70943648"
---
# <a name="asin-asinf-asinl"></a>asin, asinf, asinl

Oblicza arcus sinus.

## <a name="syntax"></a>Składnia

```C
double asin( double x );
float asinf ( float x );
long double asinl( long double x );
```

```cpp
float asin( float x );  // C++ only
long double asin( long double x );  // C++ only
```

### <a name="parameters"></a>Parametry

*x*<br/>
Wartość, której sinus ma zostać obliczony.

## <a name="return-value"></a>Wartość zwracana

Funkcja **ASIN** zwraca arcus sinus (funkcja odwrotnej sinus) *x* w zakresie od-π/2 do π/2 radianów.

Domyślnie, jeśli *x* jest mniejsza niż-1 lub większa niż 1, **ASIN** zwraca nieokreślony czas.

|Dane wejściowe|Wyjątek SEH|Wyjątek Matherr|
|-----------|-------------------|-----------------------|
|± ∞|**NIEPRAWIDŁOWY**|**_DOMAIN**|
|**QNAN**, **IND**|brak|**_DOMAIN**|
|&#124;x&#124;>1|**NIEPRAWIDŁOWY**|**_DOMAIN**|

## <a name="remarks"></a>Uwagi

Ponieważ C++ pozwala na Przeciążenie, można wywoływać przeciążenia **ASIN** z wartościami **zmiennoprzecinkowymi** i **długimi** **Double** . W programie C **ASIN** zawsze przyjmuje i zwraca wartość **Double**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek (C)|Wymagany nagłówek (C++)|
|-------------|---------------------|-|
|**ASIN**, **asinf —** , **asinl**|\<math.h>|\<cmath > lub \<Math. h >|

## <a name="example"></a>Przykład

Aby uzyskać więcej informacji, zobacz [acos, acosf —, acosl](acos-acosf-acosl.md).

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[acos, acosf, acosl](acos-acosf-acosl.md)<br/>
[atan, atanf, atanl, atan2, atan2f, atan2l](atan-atanf-atanl-atan2-atan2f-atan2l.md)<br/>
[cos, cosf, cosl](cos-cosf-cosl.md)<br/>
[_matherr](matherr.md)<br/>
[sin, sinf, sinl](sin-sinf-sinl.md)<br/>
[tan, tanf, tanl](tan-tanf-tanl.md)<br/>
