---
title: lrint, lrintf, lrintl, llrint, llrintf, llrintl
ms.date: 04/05/2018
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
helpviewer_keywords:
- lrint function
- lrintf function
- lrintl function
- llrint function
- llrintf function
- llrintl function
ms.assetid: 28ccd5b3-5e6f-434f-997d-a21d51b8ce7f
ms.openlocfilehash: a1fc404182d9d2a5cd6870fcb2cd1ff3e5f4da55
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50500847"
---
# <a name="lrint-lrintf-lrintl-llrint-llrintf-llrintl"></a>lrint, lrintf, lrintl, llrint, llrintf, llrintl

Zaokrągla wartość określoną wartość zmiennoprzecinkową do najbliższej wartości całkowitej, przy użyciu bieżącego trybu zaokrąglania i kierunku.

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
Wartość do zaokrąglenia.

## <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, zwraca zaokrąglony wartość całkowitą *x*.

|Problem|Wróć|
|-----------|------------|
|*x* znajduje się poza zakresem typu zwracanego<br /><br /> *x* = ±∞<br /><br /> *x* = NaN|Wywołuje **FE_INVALID** i zwraca wartość zero (0).|

## <a name="remarks"></a>Uwagi

Ponieważ C++ pozwala na przeciążenie, można wywoływać przeciążenia **lrint** i **llrint** o **float** i **długie**  **podwójne** typów. W programie C **lrint** i **llrint** zawsze pobierają **double**.

Jeśli *x* nie reprezentuje zmiennoprzecinkową wielokrotność wartość całkowitą, te funkcje wywołują **FE_INEXACT**.

**Specyficzne dla firmy Microsoft**: gdy wynik jest poza zakresem zwracany typ lub parametr jest NaN lub nieskończoność, wartość zwracana jest definiowany przez implementację. Kompilator Microsoft zwraca wartość zero (0).

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek języka C|Nagłówek języka C++|
|--------------|--------------|------------------|
|**lrint**, **lrintf**, **lrintl**, **llrint**, **llrintf**, **llrintl**|\<math.h>|\<cmath >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
