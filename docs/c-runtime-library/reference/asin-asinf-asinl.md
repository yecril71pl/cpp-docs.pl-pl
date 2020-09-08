---
title: asin, asinf, asinl
description: Dokumentacja interfejsu API dla ASIN, asinf — i asinl; Oblicza arcus sinus wartości zmiennoprzecinkowej.
ms.date: 08/31/2020
api_name:
- asinf
- asinl
- asin
- _o_asin
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
ms.openlocfilehash: 7167debcfb605ab05720d9441943439ea9982324
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556661"
---
# <a name="asin-asinf-asinl"></a>asin, asinf, asinl

Oblicza arcus sinus.

## <a name="syntax"></a>Składnia

```C
double asin( double x );
float asinf ( float x );
long double asinl( long double x );
#define asin(X) // Requires C11 or higher

float asin( float x );  // C++ only
long double asin( long double x );  // C++ only
```

### <a name="parameters"></a>Parametry

*y*\
Wartość, której sinus ma zostać obliczony.

## <a name="return-value"></a>Wartość zwracana

Funkcja **ASIN** zwraca arcus sinus (funkcja odwrotnej sinus) *x* w zakresie od-π/2 do π/2 radianów.

Domyślnie, jeśli *x* jest mniejsza niż-1 lub większa niż 1, **ASIN** zwraca nieokreślony czas.

|Dane wejściowe|Wyjątek SEH|Wyjątek Matherr|
|-----------|-------------------|-----------------------|
|± ∞|**Nieprawidłowy**|**_DOMAIN**|
|**QNAN**, **IND**|brak|**_DOMAIN**|
|&#124;x&#124;>1|**Nieprawidłowy**|**_DOMAIN**|

## <a name="remarks"></a>Uwagi

Ponieważ C++ pozwala na Przeciążenie, można wywoływać przeciążenia **ASIN** z **`float`** i **`long double`** wartościami. W programie C, jeśli nie używasz \<tgmath.h> makra do wywołania tej funkcji, **ASIN** zawsze przyjmuje i zwraca **`double`** .

Jeśli używasz \<tgmath.h> `asin()` makra, typ argumentu określa, która wersja funkcji jest wybrana. Aby uzyskać szczegółowe informacje, zobacz [matematyka typu ogólnego](../../c-runtime-library/tgmath.md) .

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek (C)|Wymagany nagłówek (C++)|
|-------------|---------------------|-|
|**ASIN**, **asinf —**, **asinl**|\<math.h>|\<cmath> lub \<math.h>|
|**ASIN ()** — makro | \<tgmath.h> ||

## <a name="example"></a>Przykład

Aby uzyskać więcej informacji, zobacz [acos, acosf —, acosl](acos-acosf-acosl.md).

## <a name="see-also"></a>Zobacz też

[Obsługa zmiennoprzecinkowa](../../c-runtime-library/floating-point-support.md)<br/>
[acos, acosf, acosl](acos-acosf-acosl.md)<br/>
[atan, atanf, atanl, atan2, atan2f, atan2l](atan-atanf-atanl-atan2-atan2f-atan2l.md)<br/>
[cos, cosf, cosl](cos-cosf-cosl.md)<br/>
[_matherr](matherr.md)<br/>
[sin, sinf, sinl](sin-sinf-sinl.md)<br/>
[tan, tanf, tanl](tan-tanf-tanl.md)<br/>
