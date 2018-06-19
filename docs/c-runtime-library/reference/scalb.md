---
title: _scalb —, _scalbf | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- exponential calculations
- _scalb function
- _scalbf function
- scalb function
ms.assetid: 148cf5a8-b405-44bf-a1f0-7487adba2421
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a465ca74af72a5114eac949439ab8493f89bcb39
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32406267"
---
# <a name="scalb-scalbf"></a>_scalb —, _scalbf

Skaluje argumentu przez potęgą liczby 2.

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

*EXP*<br/>
Wykładnik długich liczb całkowitych.

## <a name="return-value"></a>Wartość zwracana

Zwraca wartość wykładniczej, jeśli to się powiedzie. Na przepełnienia (w zależności od jej znaku *x*), **_scalb —** zwraca **huge_val —**; **errno** zmienna jest ustawiona na  **Erange —**.

Aby uzyskać więcej informacji dotyczących tego i innych kody powrotu, zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

**_Scalb —** funkcja oblicza wartość *x* * 2<sup>*exp*</sup>.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_scalb —**, **_scalbf**|\<float.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[ldexp](ldexp.md)<br/>
