---
title: signbit —
ms.date: 01/31/2019
f1_keywords:
- signbit
- math/signbit
helpviewer_keywords:
- signbit function
ms.openlocfilehash: ce2f632f11296bf71036011a57f242365951d7f2
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/04/2019
ms.locfileid: "55703366"
---
# <a name="signbit"></a>signbit —

Określa, czy wartość zmiennoprzecinkowa jest ujemna.

## <a name="syntax"></a>Składnia

```C
int signbit(
   /* floating-point */ x
); /* C-only macro */

inline bool signbit(
   float x
) throw(); /* C++-only overloaded function */

inline bool signbit(
   double x
) throw(); /* C++-only overloaded function */

inline bool signbit(
   long double x
) throw(); /* C++-only overloaded function */
```

### <a name="parameters"></a>Parametry

*x*<br/>
Wartość zmiennoprzecinkowa do testowania.

## <a name="return-value"></a>Wartość zwracana

**signbit —** zwraca wartość niezerową (**true** w języku C++) Jeśli argument *x* jest ujemny lub ujemna nieskończoność. Zwraca 0 (**false** w języku C++) Jeśli argument jest ujemna, dodatnią infinity lub NAN.

## <a name="remarks"></a>Uwagi

**signbit —** jest makrem, gdy skompilowano C; oraz wbudowanej przeciążonej funkcji podczas kompilowania co kod C++.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek (C)|Wymagany nagłówek (C++)|
|--------------|---------------------------|-------------------------------|
|**signbit**|\<math.h>|\<Math.h > lub \<cmath >|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[isfinite, _finite, _finitef](finite-finitef.md)<br/>
[isinf —](isinf.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[isnormal —](isnormal.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
