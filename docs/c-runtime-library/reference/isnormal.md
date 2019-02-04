---
title: isnormal —
ms.date: 01/31/2019
f1_keywords:
- isnormal
- math/isnormal
helpviewer_keywords:
- isnormal function
ms.openlocfilehash: 93e3b8912ddf20bf8e190bb42e8413e6d909bbcc
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/04/2019
ms.locfileid: "55703377"
---
# <a name="isnormal"></a>isnormal —

Określa, czy wartość zmiennoprzecinkowa jest nieskończoność.

## <a name="syntax"></a>Składnia

```C
int isnormal(
   /* floating-point */ x
); /* C-only macro */

template <class FloatingType>
inline bool isnormal(
   FloatingType x
) throw(); /* C++-only template function */
```

### <a name="parameters"></a>Parametry

*x*<br/>
Wartość zmiennoprzecinkowa do testowania.

## <a name="return-value"></a>Wartość zwracana

**isnormal —** zwraca wartość różną od zera (**true** w przypadku kodu C++) Jeśli argument *x* jest ograniczone i nie subnormal. **isnormal —** zwraca wartość 0 (**false** w przypadku kodu C++) Jeśli argument jest podnormalnych, infinity lub NAN.

## <a name="remarks"></a>Uwagi

**isnormal —** jest makrem, gdy skompilowano C; oraz wbudowanej funkcji szablonu, gdy skompilowano co kod C++.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek (C)|Wymagany nagłówek (C++)|
|--------------|---------------------------|-------------------------------|
|**isnormal —**|\<math.h>|\<Math.h > lub \<cmath >|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[isfinite, _finite, _finitef](finite-finitef.md)<br/>
[isinf —](isinf.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
