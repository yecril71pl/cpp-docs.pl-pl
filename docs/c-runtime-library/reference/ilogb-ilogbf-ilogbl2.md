---
title: ilogb —, ilogbf —, ilogbl2
ms.date: 04/05/2018
apiname:
- ilogb
- ilogbf
- ilogbl
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
ms.openlocfilehash: 272544124dd8a8a666fc434516d3c45c73b1d011
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62331680"
---
# <a name="ilogb-ilogbf-ilogbl"></a>ilogb, ilogbf, ilogbl

Pobiera całkowitą reprezentującą nieobciążonej wykładnik base 2 określoną wartość.

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
```

### <a name="parameters"></a>Parametry

*x*<br/>
Określona wartość.

## <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, zwróć wykładnik base 2 *x* jako zalogowany **int** wartość.

W przeciwnym razie zwraca jedną z następujących wartości, zdefiniowane w \<math.h >:

|Dane wejściowe|Wynik|
|-----------|------------|
|±0|FP_ILOGB0|
|±inf, ±nan czas nieokreślony|FP_ILOGBNAN|

Błędy są zgłaszane określonej [_matherr](matherr.md).

## <a name="remarks"></a>Uwagi

Ponieważ C++ pozwala na przeciążenie, można wywoływać przeciążenia **ilogb —** przyjmujące i zwracające **float** i **długie** **double** typów. W programie C **ilogb —** zawsze przyjmuje i zwraca **double**.

Wywołanie tej funkcji jest podobne do wywoływania odpowiednik **logb —** funkcji, a następnie rzutowanie zwracanej wartości **int**.

## <a name="requirements"></a>Wymagania

|Procedura|Nagłówek języka C|Nagłówek języka C++|
|-------------|--------------|------------------|
|**ilogb —**, **ilogbf —**, **ilogbl**|\<math.h>|\<cmath>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[frexp](frexp.md)<br/>
[logb, logbf, logbl, _logb, _logbf](logb-logbf-logbl-logb-logbf.md)<br/>
