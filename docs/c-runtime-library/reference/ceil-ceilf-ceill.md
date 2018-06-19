---
title: ceil ceilf —, ceill — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- ceilf
- ceil
- ceill
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
- ntdll.dll
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- ceil
- ceilf
- ceill
dev_langs:
- C++
helpviewer_keywords:
- calculating value ceilings
- ceill function
- ceil function
- ceilf function
ms.assetid: f4e5acab-5c8f-4b10-9ae2-9561e6453718
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fa68ff857db09d1426fbed6ea497624e13cc362a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32394268"
---
# <a name="ceil-ceilf-ceill"></a>ceil, ceilf, ceill

Oblicza Zaokrąglenie w górę wartość.

## <a name="syntax"></a>Składnia

```C
double ceil(
   double x
);
float ceil(
   float x
);  // C++ only
long double ceil(
   long double x
);  // C++ only
float ceilf(
   float x
);
long double ceill(
   long double x
);
```

### <a name="parameters"></a>Parametry

*x*<br/>
Wartość zmiennoprzecinkowa.

## <a name="return-value"></a>Wartość zwracana

**Ceil** zwracają wartość zmiennoprzecinkowa, która reprezentuje najmniejsza liczba całkowita, która jest większa niż lub równa *x*. Nie ma żadnych zwracany błąd.

|Dane wejściowe|Wyjątek SEH|Matherr — wyjątek|
|-----------|-------------------|-----------------------|
|GRANICACH **QNAN**, **IND**|brak|**_DOMAIN —**|

**ceil —** ma implementację, która używa Streaming SIMD Extensions 2 (SSE2). Aby uzyskać informacje i ograniczenia dotyczące korzystania z implementacji SSE2, zobacz [_set_sse2_enable —](set-sse2-enable.md).

## <a name="remarks"></a>Uwagi

Ponieważ C++ pozwala przeładowanie, można wywoływać przeciążenia **ceil** które trwają **float** lub **długi** **podwójne** typów. W programie C **ceil** zawsze przyjmuje i zwraca **podwójne**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**ceil —**, **ceilf —**, **ceill —**|\<math.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [floor](floor-floorf-floorl.md).

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[floor, floorf, floorl](floor-floorf-floorl.md)<br/>
[fmod, fmodf](fmod-fmodf.md)<br/>
[round, roundf, roundl](round-roundf-roundl.md)<br/>
