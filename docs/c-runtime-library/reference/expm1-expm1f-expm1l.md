---
title: expm1, expm1f, expm1l
ms.date: 04/05/2018
apiname:
- expm1l
- expm1
- expm1f
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
- expm1l
- expm1
- expm1f
helpviewer_keywords:
- expm1f function
- expm1l function
- expm1 function
ms.assetid: 2a4dd2d9-370c-42b0-9067-0625efa272e0
ms.openlocfilehash: 5971f879ecef7d4fa1027849cc44d598e877b5f0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50441070"
---
# <a name="expm1-expm1f-expm1l"></a>expm1, expm1f, expm1l

Oblicza eksponentę wartości, minus jeden.

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
```

### <a name="parameters"></a>Parametry

*x*<br/>
Zmiennoprzecinkowa Wartość wykładnicza.

## <a name="return-value"></a>Wartość zwracana

**Expm1 —** funkcje zwracają wartość zmiennoprzecinkową, która reprezentuje e<sup>x</sup> - 1, jeśli to się powiedzie. W przepełnieniu **expm1 —** zwraca **HUGE_VAL**, **expm1f —** zwraca **HUGE_VALF**, **expm1l —** zwraca **HUGE_VALL**, i **errno** ustawiono **ERANGE**. Aby uzyskać więcej informacji na temat kodów powrotnych, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Ponieważ C++ pozwala na przeciążenie, można wywoływać przeciążenia **expm1 —** przyjmujące i zwracające **float** i **długie** **double** wartości. W programie C **expm1 —** zawsze przyjmuje i zwraca **double**.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**expm1 —**, **expm1f —**, **expm1l —**|\<math.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[exp2, exp2f, exp2l](exp2-exp2f-exp2l.md)<br/>
[pow, powf, powl](pow-powf-powl.md)<br/>
