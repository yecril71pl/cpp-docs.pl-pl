---
title: isfinite, _finite, _finitef
ms.date: 01/31/2019
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
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- isfinite
- finite
- _finite
- _finitef
- math/isfinite
- math/_finite
- math/_finitef
- float/_finite
helpviewer_keywords:
- finite function
- _finite function
- _finitef function
ms.assetid: 5a7d7ca7-befb-4e1f-831d-28713c6eb805
ms.openlocfilehash: d727839521978be66c3dc9ee173ee2ba0a567445
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62333719"
---
# <a name="isfinite-finite-finitef"></a>isfinite, _finite, _finitef

Określa, czy wartość zmiennoprzecinkowa jest ograniczone.

## <a name="syntax"></a>Składnia

```C
int isfinite(
   /* floating-point */ x
); /* C-only macro */

template <class FloatingType>
inline bool isfinite(
   FloatingType x
) throw(); /* C++-only template function */

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

`isfinite` — Makro i `_finite` i `_finitef` funkcje zwracają wartość różna od zera, jeśli *x* jest albo normalnej lub subnormal wartością skończoną. Zwracają 0, jeśli argument jest nieskończony lub NaN. Funkcja szablonu języka C++ w tekście `isfinite` działa tak samo, ale zwraca **true** lub **false**.

## <a name="remarks"></a>Uwagi

`isfinite` jest to makro, gdy kompilowany C; oraz wbudowanej funkcji szablonu, gdy skompilowano co kod C++. `_finite` i `_finitef` funkcje są specyficzne dla firmy Microsoft. `_finitef` Funkcja tylko jest dostępna, gdy kompilowany dla x86, ARM i ARM64 platform.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek (C)|Wymagany nagłówek (C++)|
|--------------|---------------------------|-------------------------------|
|`_finite`|\<float.h > lub \<math.h >|\<float.h >, \<math.h >, \<cfloat — >, lub \<cmath >|
|`isfinite`, `_finitef`|\<math.h>|\<Math.h > lub \<cmath >|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[fpclassify](fpclassify.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
[isinf](isinf.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[isnormal](isnormal.md)<br/>
