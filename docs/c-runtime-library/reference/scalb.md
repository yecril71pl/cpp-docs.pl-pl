---
title: _scalb, _scalbf
ms.date: 04/05/2018
api_name:
- _scalb
- _scalbf
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
- scalb
- _scalb
- _scalbf
helpviewer_keywords:
- exponential calculations
- _scalb function
- _scalbf function
- scalb function
ms.assetid: 148cf5a8-b405-44bf-a1f0-7487adba2421
ms.openlocfilehash: 630a5e3db2c39cb40d31c71e6a6dfa214ed91e34
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948881"
---
# <a name="_scalb-_scalbf"></a>_scalb, _scalbf

Skaluje argument z potęgą 2.

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
Wartość zmiennoprzecinkowa o podwójnej precyzji.

*EXP*<br/>
Wykładnik długiej liczby całkowitej.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość wykładniczą, jeśli powodzenie. W przypadku przepełnienia (w zależności od znaku *x*) **_scalb** zwraca +/- **HUGE_VAL**; zmienna **errno** jest ustawiona na **ERANGE**.

Aby uzyskać więcej informacji na temat tego i innych kodów powrotnych, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Funkcja **_scalb** oblicza wartość *x* \* 2<sup>*EXP*</sup>.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_scalb**, **_scalbf**|\<float.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[ldexp](ldexp.md)<br/>
