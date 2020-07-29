---
title: isfinite, _finite, _finitef
ms.date: 01/31/2019
api_name:
- _finite
- _finitef
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
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 7e15a6619e584ff52c07048fcf591835b799587f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218705"
---
# <a name="isfinite-_finite-_finitef"></a>isfinite, _finite, _finitef

Określa, czy wartość zmiennoprzecinkowa jest skończona.

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
Wartość zmiennoprzecinkowa do przetestowania.

## <a name="return-value"></a>Wartość zwracana

`isfinite`Makro i `_finite` `_finitef` funkcje i zwracają wartość różną od zera, jeśli *x* jest wartością normalną lub nienormalną. Zwracają one wartość 0, jeśli argument jest nieskończony lub NaN. Wbudowana funkcja szablonu C++ `isfinite` zachowuje się tak samo, ale zwraca **`true`** lub **`false`** .

## <a name="remarks"></a>Uwagi

`isfinite`jest makrem kompilowanym jako C i wbudowaną funkcją szablonu kompilowaną jako C++. `_finite`Funkcje i `_finitef` są specyficzne dla firmy Microsoft. `_finitef`Funkcja jest dostępna tylko po skompilowaniu dla platform x86, ARM lub arm64.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek (C)|Wymagany nagłówek (C++)|
|--------------|---------------------------|-------------------------------|
|`_finite`|\<float.h> lub \<math.h>|\<float.h>, \<math.h> , \<cfloat> lub\<cmath>|
|`isfinite`, `_finitef`|\<math.h>|\<math.h> lub \<cmath>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Obsługa zmiennoprzecinkowa](../../c-runtime-library/floating-point-support.md)<br/>
[fpclassify](fpclassify.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
[isinf](isinf.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[isnormal](isnormal.md)<br/>
