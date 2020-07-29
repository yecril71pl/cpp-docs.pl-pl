---
title: trunc, truncf, truncl
ms.date: 04/05/2018
api_name:
- trunc
- truncf
- truncl
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
- trunc
- truncf
- truncl
- math/trunc
- math/truncf
- math/truncl
helpviewer_keywords:
- trunc function
- truncf function
- truncl function
ms.assetid: de2038ac-ac0b-483e-870c-e8992dcd4fd0
ms.openlocfilehash: b47d07cbe1e86e3f53d3a562cd5e1b3dca7f4814
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232394"
---
# <a name="trunc-truncf-truncl"></a>trunc, truncf, truncl

Określa najbliższą liczbę całkowitą, która jest mniejsza lub równa określonej wartości zmiennoprzecinkowej.

## <a name="syntax"></a>Składnia

```C
double trunc( double x );
float trunc( float x ); //C++ only
long double truncl( long double x );
```

```cpp
long double trunc( long double x ); //C++ only
float trunc( float x ); //C++ only
```

### <a name="parameters"></a>Parametry

*x*<br/>
Wartość do obcięcia.

## <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, zwraca wartość typu Integer *x*, zaokrągloną do zera.

W przeciwnym razie może zwrócić jeden z następujących elementów:

|Problem|Przesłać|
|-----------|------------|
|*x* = ± nieskończoność|x|
|*x* = ± 0|x|
|*x* = NaN|NaN|

Błędy są raportowane zgodnie z opisem w [_matherr](matherr.md).

## <a name="remarks"></a>Uwagi

Ponieważ C++ pozwala na Przeciążenie, można wywoływać przeciążenia **TRUNC —** , które pobierają i zwracają **`float`** **`long double`** typy. W programie C **TRUNC —** zawsze przyjmuje i zwraca **`double`** .

Ponieważ największe wartości zmiennoprzecinkowe są dokładnymi liczbami całkowitymi, ta funkcja nie zostanie przepełniony. Jednak może dojść do przepełnienia funkcji przez zwrócenie wartości do typu Integer.

Możesz również zaokrąglić w dół, niejawnie konwertując od zmiennoprzecinkowego na całkowity; jednak wykonanie tej operacji jest ograniczone do wartości, które mogą być przechowywane w typie docelowym.

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek języka C|Nagłówek C++|
|--------------|--------------|------------------|
|**TRUNC —**, **truncf —**, **truncl**|\<math.h>|\<cmath>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[floor, floorf, floorl](floor-floorf-floorl.md)<br/>
[ceil, ceilf, ceill](ceil-ceilf-ceill.md)<br/>
[round, roundf, roundl](round-roundf-roundl.md)<br/>
