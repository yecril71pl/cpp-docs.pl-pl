---
title: fabs, fabsf, fabsl
ms.date: 4/2/2020
api_name:
- fabsf
- fabs
- fabsl
- _o_fabs
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fabs
- fabsf
- fabsl
- "math\fabs"
- "math\fabsf"
- "math\fabsl"
helpviewer_keywords:
- absolute values
- fabsf function
- calculating absolute values
- fabs function
- fabsl function
ms.assetid: 23bca210-f408-4f5e-b46b-0ccaaec31e36
ms.openlocfilehash: 38648f2108b5202cbb355da3abab9e7dedf4dc47
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347549"
---
# <a name="fabs-fabsf-fabsl"></a>fabs, fabsf, fabsl

Oblicza wartość bezwzględną argumentu zmiennoprzecinkowego.

## <a name="syntax"></a>Składnia

```C
double fabs(
   double x
);
float fabs(
   float x
); // C++ only
long double fabs(
   long double x
); // C++ only
float fabsf(
   float x
);
long double fabsl(
   long double x
);
```

### <a name="parameters"></a>Parametry

*X*<br/>
Wartość zmiennoprzecinku.

## <a name="return-value"></a>Wartość zwracana

Funkcje **fabs** zwracają wartość bezwzględną argumentu *x*. Nie ma zwracania błędów.

|Dane wejściowe|Wyjątek SEH|Wyjątek Matherr|
|-----------|-------------------|-----------------------|
|± QNAN, IND|brak|_DOMAIN|

## <a name="remarks"></a>Uwagi

C++ umożliwia przeciążenie, dzięki czemu można wywołać przeciążenia **fabs,** jeśli zostanie uwzględniona \<cmath> nagłówka. W programie C **fabs** zawsze przyjmuje i zwraca **podwójny**plik .

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek C|Wymagany nagłówek języka C++|
|--------------|-----------------------|---------------------------|
|**fabs**, **fabsf**, **fabsl**|\<> math.h|\<cmath> lub \<math.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [abs](abs-labs-llabs-abs64.md).

## <a name="see-also"></a>Zobacz też

[Obsługa zmiennoprzecinkowej](../../c-runtime-library/floating-point-support.md)<br/>
[abs, labs, llabs, _abs64](abs-labs-llabs-abs64.md)<br/>
[_cabs](cabs.md)<br/>
