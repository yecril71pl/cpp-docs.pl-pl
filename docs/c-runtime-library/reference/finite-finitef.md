---
title: _finite —, _finitef | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _finite
- _finitef
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
- finite
- _finite
- _finitef
- math/_finite
- math/_finitef
- float/_finite
dev_langs:
- C++
helpviewer_keywords:
- finite function
- _finite function
- _finitef function
ms.assetid: 5a7d7ca7-befb-4e1f-831d-28713c6eb805
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3367f13e68aa85e53d9f5f0ee83521ef465d3996
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32396644"
---
# <a name="finite-finitef"></a>_finite —, _finitef

Określa, czy wartość zmiennoprzecinkowa jest jednak ograniczona.

## <a name="syntax"></a>Składnia

```C
int _finite(
   double x
);

int _finitef(
   float x
); /* x64 and ARM/ARM64 only */
```

### <a name="parameters"></a>Parametry

*x*<br/>
Wartość zmiennoprzecinkowa do testowania.

## <a name="return-value"></a>Wartość zwracana

Zarówno **_finite —** i **_finitef** zwrócić wartość niezerową, jeśli argument *x* jest nieskończona; będący, jeśli -INF < *x* < + INF. Zwraca 0, jeśli argument ma nieograniczony lub NAN.

## <a name="remarks"></a>Uwagi

**_Finite —** i **_finitef** funkcje są określone firmy Microsoft. **_Finitef** funkcja tylko jest dostępna, gdy skompilowanego dla x86, ARM i ARM64 platform.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek (C)|Wymaganego nagłówka (C++)|
|--------------|---------------------------|-------------------------------|
|**_finite**|\<float.h — > lub \<math.h >|\<float.h — >, \<math.h >, \<cfloat — >, lub \<cmath >|
|**_finitef**|\<math.h>|\<Math.h > lub \<cmath >|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
