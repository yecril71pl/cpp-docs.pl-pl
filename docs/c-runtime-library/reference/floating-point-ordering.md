---
title: isgreater, isgreaterequal, isless, islessequal, islessgreater, isunordered
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
ms.openlocfilehash: 907b26f4e1824d7ef5c7c1a36b4e4d8ccb74c978
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220720"
---
# <a name="isgreater-isgreaterequal-isless-islessequal-islessgreater-isunordered"></a>isgreater, isgreaterequal, isless, islessequal, islessgreater, isunordered

Określa relację porządkowania między dwiema wartościami zmiennoprzecinkowymi.

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

We wszystkich porównaniach nieskończoności tego samego znaku należy porównać jako równe. Ujemna nieskończoność jest mniejsza od dowolnej wartości lub nieskończoności dodatniej. Nieskończoność dodatnia jest większa niż jakakolwiek wartość skończone lub nieskończoność ujemna. Zera są równe niezależnie od znaku. NaNs nie są mniejsze niż lub równe żadnej wartości, łącznie z innym NaN.

Gdy żaden z argumentów nie jest NaN, porządkowanie makr **isisgreaterequal**, **isless**i **islessequal** zwracają wartość różną od **zera, jeśli**określona relacja kolejności między *x* a *y* ma wartość true. Te makra zwracają wartość 0, jeśli jeden lub oba argumenty są NaNs lub jeśli relacja kolejności ma wartość false. Formularze funkcji działają w ten sam sposób, ale zwracają **`true`** lub **`false`** .

Makro **islessgreater** zwraca wartość różną od zera, jeśli zarówno *x* , jak i *y* nie są Nans, a *x* jest albo mniejsze niż lub większe niż *y*. Zwraca wartość 0, jeśli jeden lub oba argumenty są NaNs lub wartości są równe. Formularz funkcji działa tak samo, ale zwraca **`true`** lub **`false`** .

Makro **isunordered** zwraca wartość różną od zera, jeśli zarówno *x*, *y*, jak i obie są Nans. W przeciwnym razie zwraca wartość 0. Formularz funkcji działa tak samo, ale zwraca **`true`** lub **`false`** .

## <a name="remarks"></a>Uwagi

Te operacje porównania są implementowane jako makra w przypadku skompilowania jako C, a jako wbudowane funkcje szablonu po skompilowaniu jako C++.

## <a name="requirements"></a>Wymagania

|Funkcja|Wymagany nagłówek (C)|Wymagany nagłówek (C++)|
|--------------|---------------------------|-------------------------------|
| **isgreater**isisgreaterequal, **isless**, **isgreaterequal**<br/>**islessequal**, **islessgreater**, **isunordered** | \<math.h> | \<math.h> lub \<cmath> |

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Obsługa zmiennoprzecinkowa](../../c-runtime-library/floating-point-support.md)<br/>
[isfinite, _finite, _finitef](finite-finitef.md)<br/>
[isinf](isinf.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
