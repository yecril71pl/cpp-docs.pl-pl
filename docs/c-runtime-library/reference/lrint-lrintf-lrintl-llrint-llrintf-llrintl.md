---
title: lrint, lrintf, lrintl, llrint, llrintf, llrintl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- lrint
- lrintl
- lrintf
- llrint
- llrintf
- llrintl
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
- lrint
- lrintf
- lrintl
- llrint
- llrintf
- llrintl
- math/lrint
- math/lrintf
- math/lrintl
- math/llrint
- math/llrintf
- math/llrintl
dev_langs:
- C++
helpviewer_keywords:
- lrint function
- lrintf function
- lrintl function
- llrint function
- llrintf function
- llrintl function
ms.assetid: 28ccd5b3-5e6f-434f-997d-a21d51b8ce7f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5ace427267a45c87213f62276e1d7799f27db1cd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32401262"
---
# <a name="lrint-lrintf-lrintl-llrint-llrintf-llrintl"></a>lrint, lrintf, lrintl, llrint, llrintf, llrintl

Zaokrągla określona wartość zmiennoprzecinkowa do najbliższej wartości całkowite, przy użyciu bieżącego trybu zaokrąglania i kierunku.

## <a name="syntax"></a>Składnia

```C
long int lrint(
   double x
);

long int lrint(
   float x
); //C++ only

long int lrint(
   long double x
); //C++ only

long int lrintf(
   float x
);

long int lrintl(
   long double x
);

long long int llrint(
   double x
);

long long int llrint(
   float x
); //C++ only

long long int llrint(
   long double x
); //C++ only

long long int llrintf(
   float x
);

long long int llrintl(
   long double x
);

```

### <a name="parameters"></a>Parametry

*x*<br/>
wartość do zaokrąglenia.

## <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, zwraca wartość zaokrąglony integralną *x*.

|Problem|Zwraca|
|-----------|------------|
|*x* jest poza zakresem typu zwracanego<br /><br /> *x* = ±∞<br /><br /> *x* = NaN|Zgłasza **FE_INVALID** i zwraca wartość zero (0).|

## <a name="remarks"></a>Uwagi

Ponieważ C++ pozwala przeładowanie, można wywoływać przeciążenia **lrint** i **llrint** które trwają **float** i **długi**  **Podwójna** typów. W programie C **lrint** i **llrint** zawsze pobierają **podwójne**.

Jeśli *x* nie reprezentuje zmiennoprzecinkowe odpowiednikiem wartością całkowitą, zgłoś te funkcje **FE_INEXACT**.

**Microsoft określonych**: Jeśli wynik jest poza zakresem zwracany typ lub gdy parametr infinity lub NaN, zwracana wartość jest implementacją zdefiniowane. Kompilator Microsoft zwraca wartość zero (0).

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek C|Nagłówek C++|
|--------------|--------------|------------------|
|**lrint**, **lrintf**, **lrintl**, **llrint**, **llrintf**, **llrintl**|\<math.h>|\<cmath >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
