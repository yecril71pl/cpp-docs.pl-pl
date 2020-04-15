---
title: lrint, lrintf, lrintl, llrint, llrintf, llrintl
ms.date: 4/2/2020
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 6283cffaa094af4484d48781b5bb92d0339d38d1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341664"
---
# <a name="lrint-lrintf-lrintl-llrint-llrintf-llrintl"></a>lrint, lrintf, lrintl, llrint, llrintf, llrintl

Zaokrągla określoną wartość zmiennoprzecinkową do najbliższej wartości integralnej, używając bieżącego trybu zaokrąglania i kierunku.

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

*X*<br/>
wartość do zaokrąglenia.

## <a name="return-value"></a>Wartość zwracana

Jeśli się powiedzie, zwraca zaokrągloną wartość całkowitą *x*.

|Problem|Zwraca|
|-----------|------------|
|*x* znajduje się poza zakresem typu zwrotu<br /><br /> *x* = ±∞<br /><br /> *x* = NaN|Podnosi **FE_INVALID** i zwraca zero (0).|

## <a name="remarks"></a>Uwagi

Ponieważ C++ umożliwia przeciążenie, można wywołać przeciążenia **lrint** i **llrint,** które zajmują **float** i **długie** **podwójne** typy. W programie C, **lrint** i **llrint** zawsze wziąć **podwójne**.

Jeśli *x* nie reprezentuje zmiennoprzecinkowego odpowiednika wartości integralnej, funkcje te zwiększają **FE_INEXACT**.

**Specyficzne dla firmy Microsoft:** Gdy wynik znajduje się poza zakresem typu zwracanego lub gdy parametr jest NaN lub nieskończoności, wartość zwracana jest zdefiniowana. Kompilator firmy Microsoft zwraca wartość zero (0).

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

## <a name="requirements"></a>Wymagania

|Funkcja|Nagłówek C|Nagłówek języka C++|
|--------------|--------------|------------------|
|**lrint**, **lrintf**, **lrintl**, **llrint**, **llrintf**, **llrintl**|\<> math.h|\<> cmath|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Alfabetyczne zestawienie funkcji](crt-alphabetical-function-reference.md)<br/>
