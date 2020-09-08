---
title: copysign, copysignf, copysignl, _copysign, _copysignf, _copysignl
description: Odwołanie do interfejsu API do zwracania wartości, która ma wartość jednego argumentu i znaku innego przy użyciu copysign — ()
ms.date: 9/1/2020
api_name:
- copysignf
- copysignl
- _copysignl
- _copysign
- _copysignf
- copysign
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
- _copysignl
- copysign
- copysignf
- _copysign
- copysignl
- _copysignf
helpviewer_keywords:
- copysignl function
- _copysignl function
- copysign function
- _copysignf function
- _copysign function
- copysignf function
ms.assetid: 009216d6-72a2-402d-aa6c-91d924b2c9e4
ms.openlocfilehash: 8f9ffe56e82f6a82da15fde3f8efea60fc1c0f9f
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2020
ms.locfileid: "89554867"
---
# <a name="copysign-copysignf-copysignl-_copysign-_copysignf-_copysignl"></a>copysign, copysignf, copysignl, _copysign, _copysignf, _copysignl

Zwraca wartość, która ma wielkość jednego argumentu i znak innego.

## <a name="syntax"></a>Składnia

```C
double copysign(
   double x,
   double y
);
float copysign(
   float x,
   float y
); // C++ only
long double copysign(
   long double x,
   long double y
); // C++ only
float copysignf(
   float x,
   float y
); // C++ only
long double copysignl(
   long double x,
   long double y
); // C++ only
double _copysign(
   double x,
   double y
);
long double _copysignl(
   long double x,
   long double y
);
#define copysign(X, Y) // Requires C11 or higher
```

### <a name="parameters"></a>Parametry

*y*\
Wartość zmiennoprzecinkowa, która jest zwracana jako wielkość wyniku.

*t*\
Wartość zmiennoprzecinkowa, która jest zwracana jako znak wyniku.

[Procedury obsługi zmiennoprzecinkowej](../../c-runtime-library/floating-point-support.md)

## <a name="return-value"></a>Wartość zwracana

Funkcje **copysign —** zwracają wartość zmiennoprzecinkową, która łączy rozmiar *x* i znak *y*. Nie ma żadnego powrotu błędu.

## <a name="remarks"></a>Uwagi

Ponieważ C++ pozwala na Przeciążenie, można wywoływać przeciążenia **copysign —** , które pobierają i zwracają **`float`** **`long double`** wartości. W programie C, jeśli nie używasz \<tgmath.h> makra do wywołania tej funkcji, **copysign —** zawsze przyjmuje i zwraca **`double`** .

Jeśli używasz \<tgmath.h> `copysign()` makra, typ argumentu określa, która wersja funkcji jest wybrana. Aby uzyskać szczegółowe informacje, zobacz [matematyka typu ogólnego](../../c-runtime-library/tgmath.md) .

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_copysign**|\<float.h>|
|**copysign —**, **copysignf —**, **copysignl**, **_copysignf**, **_copysignl**|\<math.h>|
|**copysign —** — makro | \<tgmath.h> |

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[fabs, fabsf, fabsl](fabs-fabsf-fabsl.md)<br/>
[_chgsign, _chgsignf, _chgsignl](chgsign-chgsignf-chgsignl.md)<br/>
