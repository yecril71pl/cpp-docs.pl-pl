---
title: expm1, expm1f, expm1l
description: Dokumentacja interfejsu API dla expm1 —, expm1f — i expm1 —; który obliczy wartość z przeliczania wartości "Base-e", minus jeden.
ms.date: 9/1/2020
api_name:
- expm1l
- expm1
- expm1f
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- expm1l
- expm1
- expm1f
helpviewer_keywords:
- expm1f function
- expm1l function
- expm1 function
ms.assetid: 2a4dd2d9-370c-42b0-9067-0625efa272e0
ms.openlocfilehash: 6d352e91d895cd63c7134faff90bc1bc43a50708
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556505"
---
# <a name="expm1-expm1f-expm1l"></a>expm1, expm1f, expm1l

Oblicza wykładniczą wartość e wartości, minus jeden.

## <a name="syntax"></a>Składnia

```C
double expm1(
   double x
);
float expm1(
   float x
);  // C++ only
long double expm1(
   long double x
);  // C++ only
float expm1f(
   float x
);
long double expm1l(
   long double x
);
#define expm1(X) // Requires C11 or higher
```

### <a name="parameters"></a>Parametry

*y*\
Wartość wykładnicza zmiennoprzecinkowa.

## <a name="return-value"></a>Wartość zwracana

Funkcje **expm1 —** zwracają wartość zmiennoprzecinkową, która reprezentuje<sup>symbol e x</sup> -1, jeśli to się powiedzie. W przypadku przepełnienia funkcja **expm1 —** zwraca **HUGE_VAL**, **expm1f —** zwraca **HUGE_VALF**, **Expm1l** zwraca **HUGE_VALL**, a **errno** jest ustawiona na **ERANGE**. Aby uzyskać więcej informacji na temat kodów powrotnych, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Ponieważ C++ pozwala na Przeciążenie, można wywoływać przeciążenia **expm1 —** , które pobierają i zwracają **`float`** **`long double`** wartości. W programie C, jeśli nie używasz \<tgmath.h> makra do wywołania tej funkcji, **expm1 —** zawsze przyjmuje i zwraca **`double`** .

Jeśli używasz \<tgmath.h> `expm1()` makra, typ argumentu określa, która wersja funkcji jest wybrana. Aby uzyskać szczegółowe informacje, zobacz [matematyka typu ogólnego](../../c-runtime-library/tgmath.md) .

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**expm1 —**, **expm1f —**, **expm1l**|\<math.h>|
|**expm1 —** — makro | \<tgmath.h> |

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Obsługa zmiennoprzecinkowa](../../c-runtime-library/floating-point-support.md)<br/>
[exp2, exp2f, exp2l](exp2-exp2f-exp2l.md)<br/>
[pow, powf, powl](pow-powf-powl.md)<br/>
