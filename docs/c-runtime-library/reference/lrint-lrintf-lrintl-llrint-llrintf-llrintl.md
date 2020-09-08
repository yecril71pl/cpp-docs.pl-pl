---
title: lrint, lrintf, lrintl, llrint, llrintf, llrintl
description: Dokumentacja interfejsu API dla lrint (), lrintf (), lrintl (), llrint (), llrintf () i llrintl (); który zaokrągla określoną wartość zmiennoprzecinkową do najbliższej wartości całkowitej przy użyciu bieżącego trybu zaokrąglania i kierunku.
ms.date: 9/1/2020
api_name:
- lrint
- lrintl
- lrintf
- llrint
- llrintf
- llrintl
- _o_llrint
- _o_llrintf
- _o_llrintl
- _o_lrint
- _o_lrintf
- _o_lrintl
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: f208c183400aac7a110bb6fd87398d4377fe8f06
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2020
ms.locfileid: "89555023"
---
# <a name="lrint-lrintf-lrintl-llrint-llrintf-llrintl"></a>lrint, lrintf, lrintl, llrint, llrintf, llrintl

Zaokrągla określoną wartość zmiennoprzecinkową do najbliższej wartości całkowitej przy użyciu bieżącego trybu zaokrąglania i kierunku.

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

#define lrint(X) // Requires C11 or higher
```

### <a name="parameters"></a>Parametry

*y*\
Wartość do zaokrąglenia.

## <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, zwraca zaokrągloną wartość całkowitą z *x*.

|Problem|Przesłać|
|-----------|------------|
|*x* jest poza zakresem typu zwracanego<br /><br /> *x* = ± ∞<br /><br /> *x* = NaN|Podnosi **FE_INVALID** i zwraca zero (0).|

## <a name="remarks"></a>Uwagi

Ponieważ C++ pozwala na Przeciążenie, można wywoływać przeciążenia **lrint** i **llrint** , które przyjmują **`float`** i **`long double`** typu. W programie C, jeśli nie używasz \<tgmath.h> makra do wywołania tej funkcji, **lrint** i **llrint** zawsze przyjmują **`double`** .

Jeśli używasz \<tgmath.h> `llrint()` makra, typ argumentu określa, która wersja funkcji jest wybrana. Aby uzyskać szczegółowe informacje, zobacz [matematyka typu ogólnego](../../c-runtime-library/tgmath.md) .

Jeśli *x* nie reprezentuje równoważnej wartości całkowitej, te funkcje zgłaszają **FE_INEXACT**.

**Specyficzne dla firmy Microsoft**: kiedy wynik znajduje się poza zakresem typu zwracanego lub gdy parametr jest NaN lub nieskończoności, wartość zwracana jest zdefiniowana przez implementację. Kompilator firmy Microsoft zwraca wartość zero (0).

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek języka C|Nagłówek C++|
|--------------|--------------|------------------|
|**lrint**, **lrintf**, **lrintl**, **llrint**, **llrintf**, **llrintl**|\<math.h>|\<cmath>|
|**lrint** — makro | \<tgmath.h> ||

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)
