---
title: _scalb, _scalbf
ms.date: 04/05/2018
apiname:
- _scalb
- _scalbf
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
- scalb
- _scalb
- _scalbf
helpviewer_keywords:
- exponential calculations
- _scalb function
- _scalbf function
- scalb function
ms.assetid: 148cf5a8-b405-44bf-a1f0-7487adba2421
ms.openlocfilehash: c3f776ec27c365601d4fe57fb6cf0a5c9b9e0cbd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62357216"
---
# <a name="scalb-scalbf"></a>_scalb, _scalbf

Argument skali przez potęgą liczby 2.

## <a name="syntax"></a>Składnia

```C
double _scalb(
   double x,
   long exp
);
float _scalbf(
   float x,
   long exp
); /* x64 only */
```

### <a name="parameters"></a>Parametry

*x*<br/>
Wartość podwójnej precyzji, zmiennoprzecinkowych.

*exp*<br/>
Wykładnik liczba całkowita typu Long.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość wykładniczą, jeśli to się powiedzie. Przy przepełnieniu (w zależności od jej znaku *x*), **_scalb —** zwraca wartość +/- **HUGE_VAL**; **errno** zmienna jest ustawiona na  **ERANGE**.

Aby uzyskać więcej informacji na temat tego i innych kodach powrotnych, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**_Scalb —** funkcja oblicza wartość *x* \* 2<sup>*exp*</sup>.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_scalb —**, **_scalbf**|\<float.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[ldexp](ldexp.md)<br/>
