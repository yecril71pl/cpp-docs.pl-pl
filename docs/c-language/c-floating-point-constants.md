---
title: Stałe zmiennoprzecinkowe języka C
ms.date: 11/04/2016
helpviewer_keywords:
- types [C], constants
- floating-point numbers, floating-point constants
- constants, floating-point
- floating-point constants
- floating-point constants, about floating-point constants
- double data type, floating-point constants
ms.assetid: e1bd9b44-d6ab-470c-93e5-07142c7a2062
ms.openlocfilehash: 5e17490926ee328c3a4ca03b1de9cb6e752959a0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325683"
---
# <a name="c-floating-point-constants"></a>Stałe zmiennoprzecinkowe języka C

"Stała zmiennoprzecinkowa" to liczba dziesiętna, która reprezentuje podpisaną liczba rzeczywista. Reprezentacja liczbą rzeczywistą podpisem zawiera całkowitą część ułamkowa część i wykładnik. Użyj stałych zmiennoprzecinkowych do reprezentowania wartości zmiennoprzecinkowych, których nie można zmienić.

## <a name="syntax"></a>Składnia

*Floating point-constant*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*ułamkowe — stała* *część wykładnik*<sub>zoptymalizowany pod kątem</sub> *liczb zmiennoprzecinkowych sufiks*<sub>zoptymalizowany pod kątem</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*digit-sequence* *exponent-part* *floating-suffix*<sub>opt</sub>

*Stała ułamkowe*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*sekwencja cyfr*<sub>zoptymalizowany pod kątem</sub> **.** *digit-sequence*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*sekwencja cyfr*  **.**

*wykładnik część*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**e** *logowania*<sub>zoptymalizowany pod kątem</sub> *sekwencję cyfr*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**e** *logowania*<sub>zoptymalizowany pod kątem</sub> *sekwencję cyfr*

*znak*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**+ -**

*digit-sequence*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*digit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*digit-sequence* *digit*

*sufiks liczb zmiennoprzecinkowych*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**f, g F, G**

Możesz pominąć cyfr przed przecinkiem dziesiętnym (część całkowitą wartość) albo cyfr po punkcie dziesiętnym (część ułamkowa), ale nie oba. Tylko wtedy, gdy zawierają wykładnik, można pozostawić się punktu dziesiętnego. Żadne znaki odstępu, można oddzielić cyfr lub znaków, stałej.

W poniższych przykładach pokazano niektóre formy stałych zmiennoprzecinkowych i wyrażenia:

```C
15.75
1.575E1   /* = 15.75   */
1575e-2   /* = 15.75   */
-2.5e-3   /* = -0.0025 */
25E-4     /* =  0.0025 */
```

Stałe zmiennoprzecinkowe są pozytywne, chyba że są poprzedzone znakiem minus (**-**). W tym przypadku znak minus jest traktowany jako Jednoargumentowy operator arytmetyczny negacji. Stałe zmiennoprzecinkowe mają typ `float`, `double`, lub `long double`.

Stała zmiennoprzecinkowa bez **f**, **F**, **l**, lub **L** sufiks ma typ `double`. Jeśli litera **f** lub **F** jest sufiksem, stałej ma typ `float`. Jeśli sufiks za pomocą litery **l** lub **L**, ma typ `long double`. Na przykład:

```C
10.0L  /* Has type long double  */
10.0F  /* Has type float        */
```

Należy zauważyć, że kompilator Microsoft C: wewnętrznie reprezentuje `long double` taki sam jak typ `double`. Zobacz [magazyn typów podstawowych](../c-language/storage-of-basic-types.md) informacji o typie `double`, `float`, i `long double`.

Jak pokazano w poniższych przykładach, można pominąć część całkowitą stałej zmiennoprzecinkowej. Liczba.75 może być wyrażona w na wiele sposobów, w tym następujące:

```C
.0075e2
0.075e1
.075e1
75e-2
```

## <a name="see-also"></a>Zobacz także

[Stałe języka C](../c-language/c-constants.md)
