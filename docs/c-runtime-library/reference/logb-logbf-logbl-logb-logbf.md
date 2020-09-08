---
title: logb, logbf, logbl, _logb, _logbf
description: Dokumentacja interfejsu API dla logb —, logbf —, logbl, _logb i _logbf; wyodrębnianie wartości wykładnika argumentu zmiennoprzecinkowego.
ms.date: 9/1/2020
api_name:
- logb
- _logb
- _logbl
- logbf
- _logbf
- logbl
- _o__logb
- _o_logb
- _o_logbf
- _o_logbl
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
- logb
- logbl
- _logb
- _logbf
- logbf
helpviewer_keywords:
- _logbf function
- mantissas, floating-point variables
- logbf function
- _logb function
- exponent, floating-point numbers
- logbl function
- logb function
- floating-point functions
- floating-point functions, mantissa and exponent
- exponents and mantissas
ms.assetid: 780c4daa-6fe6-4fbc-9412-4c1ba1a1766f
ms.openlocfilehash: 1131fda94e4748d2fb2f2197f68966aaacc11d05
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556217"
---
# <a name="logb-logbf-logbl-_logb-_logbf"></a>logb, logbf, logbl, _logb, _logbf

Wyodrębnia wartość wykładnika argumentu zmiennoprzecinkowego.

## <a name="syntax"></a>Składnia

```C
double logb(
   double x
);
float logb(
   float x
); // C++ only
long double logb(
   long double x
); // C++ only
float logbf(
   float x
);
long double logbl(
   long double x
);
double _logb(
   double x
);
float _logbf(
   float x
);
#define logb(X) // Requires C11 or higher
```

### <a name="parameters"></a>Parametry

*y*\
Wartość zmiennoprzecinkowa.

## <a name="return-value"></a>Wartość zwracana

**logb —** zwraca wartość wykładnika nieobciążonego *x* jako liczbę całkowitą ze znakiem reprezentowane jako wartość zmiennoprzecinkową.

## <a name="remarks"></a>Uwagi

Funkcje **logb —** wyodrębniają wartość wykładniczą argumentu *x*zmiennoprzecinkowego, tak jakby *x* były reprezentowane z nieskończonym zakresem. Jeśli argument *x* jest nieznormalizowany, jest traktowany tak, jakby był znormalizowany.

Ponieważ C++ pozwala na Przeciążenie, można wywoływać przeciążenia **logb —** , które pobierają i zwracają **`float`** **`long double`** wartości. W programie C, jeśli nie używasz \<tgmath.h> makra do wywołania tej funkcji, **logb —** zawsze przyjmuje i zwraca **`double`** .

Jeśli używasz \<tgmath.h> `logb()` makra, typ argumentu określa, która wersja funkcji jest wybrana. Aby uzyskać szczegółowe informacje, zobacz [matematyka typu ogólnego](../../c-runtime-library/tgmath.md) .

|Dane wejściowe|Wyjątek SEH|Wyjątek Matherr|
|-----------|-------------------|-----------------------|
|QNAN, IND|Brak|_DOMAIN|
|± 0|ZERODIVIDE|_SING|

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_logb**|\<float.h>|
|**logb —**, **logbf —**, **logbl**, **_logbf**|\<math.h>|
|**logb —** — makro | \<tgmath.h> |

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Biblioteki

Wszystkie wersje [bibliotek uruchomieniowych języka C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Zobacz też

[Obsługa zmiennoprzecinkowa](../../c-runtime-library/floating-point-support.md)<br/>
[frexp](frexp.md)<br/>
