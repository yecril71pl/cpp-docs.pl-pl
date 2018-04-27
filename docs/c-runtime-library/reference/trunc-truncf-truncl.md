---
title: TRUNC truncf —, truncl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- trunc function
- truncf function
- truncl function
ms.assetid: de2038ac-ac0b-483e-870c-e8992dcd4fd0
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b958046a773fff107ec7ad782186a3923c01e149
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="trunc-truncf-truncl"></a>trunc, truncf, truncl

Określa najbliższej liczby całkowitej, która jest mniejsza lub równa określonej wartości zmiennoprzecinkowych.

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

|Problem|Zwraca|
|-----------|------------|
|*x* = ±INFINITY|x|
|*x* = ±0|x|
|*x* = NaN|NaN|

Błędy są zgłaszane jak określono w [_matherr —](matherr.md).

## <a name="remarks"></a>Uwagi

Ponieważ C++ pozwala przeładowanie, można wywoływać przeciążenia **trunc** który przyjmować i zwracać **float** i **długi** **podwójne** typów. W programie C **trunc** zawsze przyjmuje i zwraca **podwójne**.

Ponieważ największych wartości zmiennoprzecinkowe są dokładne liczb całkowitych, ta funkcja nie będzie przepełnienie samodzielnie. Może jednak spowodować przepełnienie buforu, zwracając wartość do typu integer funkcji.

Można również zaokrąglenie konwertując niejawnie z zmiennoprzecinkowe do całkowitych; jednak zrobić to jest ograniczona do wartości, które mogą być przechowywane w typie docelowym.

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek C|Nagłówek C++|
|--------------|--------------|------------------|
|**TRUNC**, **truncf —**, **truncl**|\<math.h>|\<cmath >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
[floor, floorf, floorl](floor-floorf-floorl.md)<br/>
[ceil, ceilf, ceill](ceil-ceilf-ceill.md)<br/>
[round, roundf, roundl](round-roundf-roundl.md)<br/>
