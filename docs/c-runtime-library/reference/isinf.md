---
title: isinf —
ms.date: 01/31/2019
f1_keywords:
- isinf
- math/isinf
helpviewer_keywords:
- isinf function
ms.openlocfilehash: be99970a0c7b152ba213eabd59b53a7503cd3c54
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62331613"
---
# <a name="isinf"></a>isinf —

Określa, czy wartość zmiennoprzecinkowa jest nieskończoność.

## <a name="syntax"></a>Składnia

```C
int isinf(
   /* floating-point */ x
); /* C-only macro */

template <class FloatingType>
inline bool isinf(
   FloatingType x
) throw(); /* C++-only template function */
```

### <a name="parameters"></a>Parametry

*x*<br/>
Wartość zmiennoprzecinkowa do testowania.

## <a name="return-value"></a>Wartość zwracana

**isinf —** zwraca wartość różną od zera (**true** w przypadku kodu C++) Jeśli argument *x* jest nieskończoności dodatniej lub ujemnej. **isinf —** zwraca wartość 0 (**false** w przypadku kodu C++), jeśli argument ma skończoną lub NAN. Normalne i subnormal różne wartości zmiennoprzecinkowe są traktowane jako skończoną.

## <a name="remarks"></a>Uwagi

**isinf —** jest makrem, gdy skompilowano C; oraz wbudowanej funkcji szablonu, gdy skompilowano co kod C++.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek (C)|Wymagany nagłówek (C++)|
|--------------|---------------------------|-------------------------------|
|**isinf**|\<math.h>|\<Math.h > lub \<cmath >|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[fpclassify](fpclassify.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
[isfinite, _finite, _finitef](finite-finitef.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[isnormal](isnormal.md)<br/>
