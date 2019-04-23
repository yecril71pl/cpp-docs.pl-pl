---
title: isnormal —
ms.date: 01/31/2019
f1_keywords:
- isnormal
- math/isnormal
helpviewer_keywords:
- isnormal function
ms.openlocfilehash: e426fbce71efff1e810a03b8347e7c48aa0d91d2
ms.sourcegitcommit: 14b292596bc9b9b883a9c58cd3e366b282a1f7b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60124684"
---
# <a name="isnormal"></a>isnormal —

Określa, czy wartość zmiennoprzecinkowa jest normalna wartość.

## <a name="syntax"></a>Składnia

```C
int isnormal(
   /* floating-point */ x
); /* C-only macro */

template <class FloatingType>
inline bool isnormal(
   FloatingType x
) throw(); /* C++-only function template */
```

### <a name="parameters"></a>Parametry

*x*<br/>
Wartość zmiennoprzecinkowa do testowania.

## <a name="return-value"></a>Wartość zwracana

**isnormal —** zwraca wartość różną od zera (**true** w C++ kodu) Jeśli argument *x* jest zero, podnormalnych, nieskończone ani jest NaN. W przeciwnym razie **isnormal —** zwraca wartość 0 (**false** w C++ kodu).

## <a name="remarks"></a>Uwagi

**isnormal —** jest makrem, gdy kompilowany jako C i wbudowany szablon funkcji, gdy kompilowany jako C++.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek (C)|Wymagany nagłówek (C++)|
|--------------|---------------------------|-------------------------------|
|**isnormal**|\<math.h>|\<Math.h > lub \<cmath >|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[isfinite, _finite, _finitef](finite-finitef.md)<br/>
[isinf](isinf.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
