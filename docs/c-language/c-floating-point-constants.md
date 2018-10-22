---
title: Stałe zmiennoprzecinkowe języka C | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- types [C], constants
- floating-point numbers, floating-point constants
- constants, floating-point
- floating-point constants
- floating-point constants, about floating-point constants
- double data type, floating-point constants
ms.assetid: e1bd9b44-d6ab-470c-93e5-07142c7a2062
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 23b5db965c8b4e29e8d25bad658189e7b37fc929
ms.sourcegitcommit: f9d9db80a8f13eae2c41337b974e1298109e33c5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2018
ms.locfileid: "49640771"
---
# <a name="c-floating-point-constants"></a>Stałe zmiennoprzecinkowe języka C

"Stała zmiennoprzecinkowa" to liczba dziesiętna, która reprezentuje podpisaną liczba rzeczywista. Reprezentacja liczbą rzeczywistą podpisem zawiera całkowitą część ułamkowa część i wykładnik. Użyj stałych zmiennoprzecinkowych do reprezentowania wartości zmiennoprzecinkowych, których nie można zmienić.

## <a name="syntax"></a>Składnia

*Floating point-constant*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*ułamkowe — stała* *część wykładnik*<sub>zoptymalizowany pod kątem</sub> *liczb zmiennoprzecinkowych sufiks*<sub>zoptymalizowany pod kątem</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*sekwencja cyfr* *część wykładnik* *liczb zmiennoprzecinkowych sufiks*<sub>zoptymalizowany pod kątem</sub>

*Stała ułamkowe*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*sekwencja cyfr*<sub>zoptymalizowany pod kątem</sub> **.** *sekwencja cyfr*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*sekwencja cyfr***.**

*wykładnik część*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**e** *logowania*<sub>zoptymalizowany pod kątem</sub> *sekwencję cyfr*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**e** *logowania*<sub>zoptymalizowany pod kątem</sub> *sekwencję cyfr*

*znak*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**+ -**

*sekwencja cyfr*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*cyfra*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*sekwencja cyfr* *cyfra*

*sufiks liczb zmiennoprzecinkowych*: jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**f, g F, G**

Możesz pominąć cyfr przed przecinkiem dziesiętnym (część całkowitą wartość) albo cyfr po punkcie dziesiętnym (część ułamkowa), ale nie oba. Tylko wtedy, gdy zawierają wykładnik, można pozostawić się punktu dziesiętnego. Żadne znaki odstępu, można oddzielić cyfr lub znaków, stałej.

W poniższych przykładach pokazano niektóre formy stałych zmiennoprzecinkowych i wyrażenia:

```
15.75
1.575E1   /* = 15.75   */
1575e-2   /* = 15.75   */
-2.5e-3   /* = -0.0025 */
25E-4     /* =  0.0025 */
```

Stałe zmiennoprzecinkowe są pozytywne, chyba że są poprzedzone znakiem minus (**-**). W tym przypadku znak minus jest traktowany jako Jednoargumentowy operator arytmetyczny negacji. Stałe zmiennoprzecinkowe mają typ `float`, `double`, lub `long double`.

Stała zmiennoprzecinkowa bez **f**, **F**, **l**, lub **L** sufiks ma typ `double`. Jeśli litera **f** lub **F** jest sufiksem, stałej ma typ `float`. Jeśli sufiks za pomocą litery **l** lub **L**, ma typ `long double`. Na przykład:

```
100L  /* Has type long double  */
100F  /* Has type float        */
```

Należy zauważyć, że kompilator Microsoft C: wewnętrznie reprezentuje `long double` taki sam jak typ `double`. Zobacz [magazyn typów podstawowych](../c-language/storage-of-basic-types.md) informacji o typie `double`, `float`, i `long double`.

Jak pokazano w poniższych przykładach, można pominąć część całkowitą stałej zmiennoprzecinkowej. Liczba.75 może być wyrażona w na wiele sposobów, w tym następujące:

```
.0075e2
0.075e1
.075e1
75e-2
```

## <a name="see-also"></a>Zobacz też

[Stałe języka C](../c-language/c-constants.md)
