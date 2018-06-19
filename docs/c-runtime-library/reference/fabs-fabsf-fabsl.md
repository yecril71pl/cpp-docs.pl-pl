---
title: fabs — fabsf —, fabsl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- fabsf
- fabs
- fabsl
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
- fabs
- fabsf
- fabsl
- "math\fabs"
- "math\fabsf"
- "math\fabsl"
dev_langs:
- C++
helpviewer_keywords:
- absolute values
- fabsf function
- calculating absolute values
- fabs function
- fabsl function
ms.assetid: 23bca210-f408-4f5e-b46b-0ccaaec31e36
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e97d8eef45c53c119fef663420ae70b4b4762e3e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32395728"
---
# <a name="fabs-fabsf-fabsl"></a>fabs —, fabsf —, fabsl

Oblicza wartość bezwzględną liczby zmiennoprzecinkowej argumentu.

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

*x*<br/>
Wartość zmiennoprzecinkowa.

## <a name="return-value"></a>Wartość zwracana

**Fabs —** zwracają wartość bezwzględna argumentu *x*. Nie ma żadnych zwracany błąd.

|Dane wejściowe|Wyjątek SEH|Matherr — wyjątek|
|-----------|-------------------|-----------------------|
|GRANICACH QNAN, IND|brak|_DOMAIN|

## <a name="remarks"></a>Uwagi

C++ pozwala przeładowanie, dlatego można wywoływać przeciążenia **fabs —** Jeśli dołączysz \<cmath > nagłówka. W programie C **fabs —** zawsze przyjmuje i zwraca **podwójne**.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek C|Wymagany nagłówek C++|
|--------------|-----------------------|---------------------------|
|**fabs —**, **fabsf —**, **fabsl**|\<math.h>|\<cmath > lub \<math.h >|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [abs](abs-labs-llabs-abs64.md).

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[abs, labs, llabs, _abs64](abs-labs-llabs-abs64.md)<br/>
[_cabs](cabs.md)<br/>
