---
title: isgreater isgreaterequal, isless, islessequal, islessgreater, isunordered
ms.date: 01/31/2019
f1_keywords:
- isgreater
- math/isgreater
- isgreaterequal
- math/isgreaterequal
- isless
- math/isless
- islessequal
- math/islessequal
- islessgreater
- math/islessgreater
- isunordered
- math/isunordered
helpviewer_keywords:
- isgreater function
- isgreaterequal function
- isless function
- islessequal function
- islessgreater function
- isunordered function
ms.openlocfilehash: 748360cae1dd0ee43645dee369c60c835246ed03
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/04/2019
ms.locfileid: "55703381"
---
# <a name="isgreater-isgreaterequal-isless-islessequal-islessgreater-isunordered"></a>isgreater isgreaterequal, isless, islessequal, islessgreater, isunordered

Określa szeregowania relację między dwiema wartościami zmiennoprzecinkowych.

## <a name="syntax"></a>Składnia

```C
int isgreater(
   /* floating-point */ x,
   /* floating-point */ y
); /* C-only macro */

int isgreaterequal(
   /* floating-point */ x,
   /* floating-point */ y
); /* C-only macro */

int isless(
   /* floating-point */ x,
   /* floating-point */ y
); /* C-only macro */

int islessequal(
   /* floating-point */ x,
   /* floating-point */ y
); /* C-only macro */

int islessgreater(
   /* floating-point */ x,
   /* floating-point */ y
); /* C-only macro */

int isunordered(
   /* floating-point */ x,
   /* floating-point */ y
); /* C-only macro */
```

```C++
template <class FloatingType1, class FloatingType2>
inline bool isgreater(
   FloatingType1 x,
   FloatingType2 y
) throw(); /* C++-only template function */

template <class FloatingType1, class FloatingType2>
inline bool isgreaterequal(
   FloatingType1 x,
   FloatingType2 y
) throw(); /* C++-only template function */

template <class FloatingType1, class FloatingType2>
inline bool isless(
   FloatingType1 x,
   FloatingType2 y
) throw(); /* C++-only template function */

template <class FloatingType1, class FloatingType2>
inline bool islessequal(
   FloatingType1 x,
   FloatingType2 y
) throw(); /* C++-only template function */

template <class FloatingType1, class FloatingType2>
inline bool islessgreater(
   FloatingType1 x,
   FloatingType2 y
) throw(); /* C++-only template function */

template <class FloatingType1, class FloatingType2>
inline bool isunordered(
   FloatingType1 x,
   FloatingType2 y
) throw(); /* C++-only template function */
```

### <a name="parameters"></a>Parametry

*x*, *y*<br/>
Wartości zmiennoprzecinkowe do porównania.

## <a name="return-value"></a>Wartość zwracana

Wszystkie porównania porównuje nieskończoności ten sam znak jako równe. Minus nieskończoności jest mniejsza niż wartość skończoną ani nieskończoności dodatniej. Nieskończoności dodatniej jest większa niż wartość skończoną ani ujemna nieskończoność. Wartości zerowe są takie same, niezależnie od tego znaku. NaNs nie jest mniejsza, równa lub większa niż dowolne wartości, w tym innego NaN.

Jeśli żaden argument jest NaN, makra szeregowania **isgreater**, **isgreaterequal**, **isless**, i **islessequal** zwracają różna od zera Jeśli określonej relacji szeregowania między *x* i *y* prawdziwe. Te makra zwraca 0, jeśli jeden lub oba argumenty są NaNs lub szeregowania relacji ma wartość false. Formularze funkcja zachowują się tak samo, ale powróci **true** lub **false**.

**Islessgreater** makro zwraca wartość niezerową, jeśli obie *x* i *y* nie są NaNs, i *x* jest mniejsza niż lub równa *y*. Zwraca 0, jeśli jeden lub oba argumenty są NaNs lub jeśli wartości są równe. Formularz funkcja działa tak samo, ale zwraca **true** lub **false**.

**Isunordered** — makro zwraca wartość niezerową, jeśli *x*, *y*, lub jedne i drugie są NaNs. W przeciwnym razie zwraca wartość 0. Formularz funkcja działa tak samo, ale zwraca **true** lub **false**.

## <a name="remarks"></a>Uwagi

Te operacje porównania są implementowane jako makra, gdy skompilowano C, jak i wbudowane funkcje szablonu, gdy skompilowano co kod C++.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek (C)|Wymagany nagłówek (C++)|
|--------------|---------------------------|-------------------------------|
| **isgreater**, **isgreaterequal**, **isless**,<br/>**islessequal**, **islessgreater**, **isunordered** | \<math.h> | \<Math.h > lub \<cmath > |

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[isfinite, _finite, _finitef](finite-finitef.md)<br/>
[isinf —](isinf.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
