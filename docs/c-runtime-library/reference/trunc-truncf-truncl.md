---
title: trunc, truncf, truncl
ms.date: 04/05/2018
apiname:
- trunc
- truncf
- truncl
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
ms.openlocfilehash: 6e023b9d894ea1b40a0e056e73b7c32f1e3cbed7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50519863"
---
# <a name="trunc-truncf-truncl"></a>trunc, truncf, truncl

Określa najbliższej liczby całkowitej, która jest mniejsza niż lub równa określonej wartości zmiennoprzecinkowych.

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

Jeśli to się powiedzie, zwraca wartość całkowitą *x*zaokrągloną w kierunku zera.

W przeciwnym razie może zwracać jedną z następujących czynności:

|Problem|Wróć|
|-----------|------------|
|*x* = ±INFINITY|x|
|*x* = ±0|x|
|*x* = NaN|NaN|

Błędy są zgłaszane określonej [_matherr](matherr.md).

## <a name="remarks"></a>Uwagi

Ponieważ C++ pozwala na przeciążenie, można wywoływać przeciążenia **trunc** przyjmujące i zwracające **float** i **długie** **double** typów. W programie C **trunc** zawsze przyjmuje i zwraca **double**.

Ponieważ największej wartości zmiennoprzecinkowe są dokładne liczb całkowitych, ta funkcja nie będzie przepełnienia samodzielnie. Może jednak spowodować przepełnienie buforu, zwracając wartość do typu całkowitego funkcji.

Można również zaokrąglenie konwertując niejawnie z zmiennoprzecinkowe do całkowitych; Spowoduje to więc jest jednak ograniczona do wartości, które mogą być przechowywane w typie docelowym.

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek języka C|Nagłówek języka C++|
|--------------|--------------|------------------|
|**TRUNC —**, **truncf —**, **truncl**|\<math.h>|\<cmath >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[floor, floorf, floorl](floor-floorf-floorl.md)<br/>
[ceil, ceilf, ceill](ceil-ceilf-ceill.md)<br/>
[round, roundf, roundl](round-roundf-roundl.md)<br/>
