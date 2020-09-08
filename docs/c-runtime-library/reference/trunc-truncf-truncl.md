---
title: trunc, truncf, truncl
description: Dokumentacja interfejsu API dla TRUNC —, truncf —, truncl; która określa najbliższą liczbę całkowitą, która jest mniejsza lub równa określonej wartości zmiennoprzecinkowej.
ms.date: 9/1/2020
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
ms.openlocfilehash: f1f2fde95bb944aa461bb95a9ad30fac204552b9
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556635"
---
# <a name="trunc-truncf-truncl"></a>trunc, truncf, truncl

Określa najbliższą liczbę całkowitą, która jest mniejsza lub równa określonej wartości zmiennoprzecinkowej.

## <a name="syntax"></a>Składnia

```C
double trunc( double x );
long double truncl( long double x );
#define trunc(X) // Requires C11 or higher

long double trunc( long double x ); //C++ only
float trunc( float x ); //C++ only
```

### <a name="parameters"></a>Parametry

*y*\
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

Ponieważ C++ pozwala na Przeciążenie, można wywoływać przeciążenia **TRUNC —** , które pobierają i zwracają **`float`** **`long double`** typy. W programie C, jeśli nie używasz \<tgmath.h> makra do wywołania tej funkcji, **TRUNC —** zawsze przyjmuje i zwraca **`double`** .

Jeśli używasz \<tgmath.h> `trunc()` makra, typ argumentu określa, która wersja funkcji jest wybrana. Aby uzyskać szczegółowe informacje, zobacz [matematyka typu ogólnego](../../c-runtime-library/tgmath.md) .

Ponieważ największe wartości zmiennoprzecinkowe są dokładnymi liczbami całkowitymi, ta funkcja nie zostanie przepełniony. Jednak może dojść do przepełnienia funkcji przez zwrócenie wartości do typu Integer.

Możesz również zaokrąglić w dół, niejawnie konwertując od zmiennoprzecinkowego na całkowity; jednak wykonanie tej operacji jest ograniczone do wartości, które mogą być przechowywane w typie docelowym.

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek języka C|Nagłówek C++|
|--------------|--------------|------------------|
|**TRUNC —**, **truncf —**, **truncl**|\<math.h>|\<cmath>|
|**TRUNC —** — makro | \<tgmath.h> ||

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[floor, floorf, floorl](floor-floorf-floorl.md)<br/>
[ceil, ceilf, ceill](ceil-ceilf-ceill.md)<br/>
[round, roundf, roundl](round-roundf-roundl.md)<br/>
