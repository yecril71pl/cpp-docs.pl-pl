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
ms.openlocfilehash: 8777f04b047516ef29ae7bf67ddaf4195e3aaf6e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228027"
---
# <a name="c-floating-point-constants"></a>Stałe zmiennoprzecinkowe języka C

"Stała zmiennoprzecinkowa" jest liczbą dziesiętną, która reprezentuje podpisany numer rzeczywisty. Reprezentacja podpisanej liczby rzeczywistej zawiera część całkowitą, część ułamkową i wykładnik. Używaj stałych zmiennoprzecinkowych do reprezentowania wartości zmiennoprzecinkowych, których nie można zmienić.

## <a name="syntax"></a>Składnia

*zmiennoprzecinkowe — stała*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;dwuargumentowy *—* *wykładnik*<sub>opt</sub> stałej —<sub>wybór</sub> *sufiksu zmiennoprzecinkowego*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wykładnik* *sekwencji cyfr* —<sub>wybór</sub> *sufiksu zmiennoprzecinkowego*części

*stała ułamkowa*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wybór sekwencji cyfr*<sub>opt</sub> **.** *Sekwencja cyfr*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*sekwencja cyfr*  **.**

*część wykładnika*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;cyfra za *podpisanie*<sub>opt</sub> **e** *-sekwencji*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Cyfra za *podpisanie*<sub>opt</sub> **E** *-sekwencji*

*znak*: jedno z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**+ -**

*sekwencja cyfr*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*kontrol*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*cyfra* *cyfra*

*sufiks zmiennoprzecinkowy*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**f l l**

Możesz pominąć cyfry przed punktem dziesiętnym (część całkowitą wartości) lub cyfry po przecinku dziesiętnym (części ułamkowej), ale nie oba. Możesz opuścić punkt dziesiętny tylko wtedy, gdy dołączysz wykładnik. Znaki odstępu nie mogą oddzielić cyfr ani znaków stałej.

Poniższe przykłady ilustrują niektóre formy stałych i wyrażeń zmiennoprzecinkowych:

```C
15.75
1.575E1   /* = 15.75   */
1575e-2   /* = 15.75   */
-2.5e-3   /* = -0.0025 */
25E-4     /* =  0.0025 */
```

Stałe zmiennoprzecinkowe są dodatnie, chyba że są poprzedzone znakiem minus ( **-** ). W takim przypadku znak minus jest traktowany jako jednoargumentowy operator negacji arytmetycznej. Stałe zmiennoprzecinkowe mają typ **`float`** , **`double`** lub **`long double`** .

Stała zmiennoprzecinkowa bez sufiksu **f**, **f**, **l**lub **l** ma typ **`double`** . Jeśli litera **f** lub **f** jest sufiksem, stała ma typ **`float`** . Jeśli sufiks jest poprzedzony literą **l** lub **l**, ma typ **`long double`** . Na przykład:

```C
10.0L  /* Has type long double  */
10.0F  /* Has type float        */
```

Należy zauważyć, że kompilator języka Microsoft C wewnętrznie reprezentuje ten **`long double`** sam typ **`double`** . Zobacz [Magazyn typów podstawowych](../c-language/storage-of-basic-types.md) , aby uzyskać informacje o typie **`double`** , **`float`** i **`long double`** .

Można pominąć część całkowitą stałej zmiennoprzecinkowej, jak pokazano w poniższych przykładach. Liczba. 75 może być wyrażona na wiele sposobów, w tym:

```C
.0075e2
0.075e1
.075e1
75e-2
```

## <a name="see-also"></a>Zobacz także

[Stałe języka C](../c-language/c-constants.md)
