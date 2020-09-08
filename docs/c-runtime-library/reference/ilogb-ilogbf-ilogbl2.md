---
title: ilogb, ilogbf, ilogbl2
description: Dokumentacja interfejsu API dla ilogb —, ilogbf — i ilogbl2; który pobiera liczbę całkowitą, która reprezentuje nieobciążone wykładnię bazową (2) określonej wartości.
ms.date: 9/1/2020
api_name:
- ilogb
- ilogbf
- ilogbl
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
- ilogb
- ilogbf
- ilogbl
- math/ilogb
- math/ilogbf
- math/ilogbl
helpviewer_keywords:
- ilogb function
- ilogbf function
- ilogbl function
ms.assetid: 9ef19d57-1caa-41d5-8233-2faad3562fcb
ms.openlocfilehash: b27c329cca1edb9d30bb6b9b641f94d174c9c406
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556375"
---
# <a name="ilogb-ilogbf-ilogbl"></a>ilogb, ilogbf, ilogbl

Pobiera liczbę całkowitą, która reprezentuje nieobciążone wykładnik podstawowy-2 określonej wartości.

## <a name="syntax"></a>Składnia

```C
int ilogb(
   double x
);

int ilogb(
   float x
); //C++ only

int ilogb(
   long double x
); //C++ only

int ilogbf(
   float x
);

int ilogbl(
   long double x
);

#define ilogbl(X) // Requires C11 or higher
```

### <a name="parameters"></a>Parametry

*y*\
Określona wartość.

## <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, zwróć wartość typu " *x* 2" w postaci **`signed int`** wartości.

W przeciwnym razie zwraca jedną z następujących wartości zdefiniowanych w \<math.h> :

|Dane wejściowe|Wynik|
|-----------|------------|
|± 0|FP_ILOGB0|
|± inf, ± NaN, nieokreślony|FP_ILOGBNAN|

Błędy są raportowane zgodnie z opisem w [_matherr](matherr.md).

## <a name="remarks"></a>Uwagi

Ponieważ C++ pozwala na Przeciążenie, można wywoływać przeciążenia **ilogb —** , które pobierają i zwracają **`float`** **`long double`** typy. W programie C, jeśli nie używasz \<tgmath.h> makra do wywołania tej funkcji, **ilogb —** zawsze przyjmuje i zwraca **`double`** .

Jeśli używasz \<tgmath.h> `ilogb()` makra, typ argumentu określa, która wersja funkcji jest wybrana. Aby uzyskać szczegółowe informacje, zobacz [matematyka typu ogólnego](../../c-runtime-library/tgmath.md) .

Wywołanie tej funkcji jest podobne do wywołania równoważnej funkcji **logb —** , a następnie rzutowania wartości zwracanej na **`int`** .

## <a name="requirements"></a>Wymagania

|Procedura|Nagłówek języka C|Nagłówek C++|
|-------------|--------------|------------------|
|**ilogb —**, **ilogbf —**, **ilogbl**|\<math.h>|\<cmath>|
|**ilogb —** — makro | \<tgmath.h> ||

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[frexp](frexp.md)<br/>
[logb, logbf, logbl, _logb, _logbf](logb-logbf-logbl-logb-logbf.md)<br/>
