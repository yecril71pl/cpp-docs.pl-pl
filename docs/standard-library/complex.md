---
title: '&lt;złożone&gt; | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <complex>
- std::<complex>
dev_langs:
- C++
helpviewer_keywords:
- complex header
ms.assetid: 5e728995-3059-496a-9ce9-61d1bfbe4f2b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a29dfc976ca29405814bbae81f42a02a74300d74
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="ltcomplexgt"></a>&lt;complex&gt;

Definiuje klasę szablonu kontenera **złożonych** i jego obsługi szablonów.

## <a name="syntax"></a>Składnia

```cpp
#include <complex>
```

## <a name="remarks"></a>Uwagi

Liczba złożonych jest uporządkowanej pary liczb rzeczywistych. W sposób całkowicie geometryczne płaszczyzna złożone jest prawdziwe, dwuwymiarowa płaszczyzny. Specjalne jakości płaszczyzny złożone, które odróżniający go od rzeczywistych osi są spowodowane o dodatkowe algebraicznych struktury. Ta struktura algebraicznych ma dwie podstawowe operacje:

- Dodanie zdefiniowany jako (*a*, *b*) + (*c*, *d*) = (*a* + *c* , *b* + *d*)

- Zdefiniowany jako mnożenia (*a*, *b*) \* (*c*, *d*) = (*ac*  -  *bd*, *ad* + *bc*)

Zbiór liczb złożone z operacjami Dodawanie złożone i mnożenie złożone są pola w tym sensie algebraicznych standardowe:

- Operacje dodawania i mnożenia to przemienne i asocjacyjnej i mnożenia dystrybuuje przez dodanie dokładnie tak jak w przypadku dodaniu prawdziwe i mnożenia pola liczb rzeczywistych.

- Liczba złożonych (0, 0) jest tożsamość dodatku i (1, 0) jest mnożenia tożsamości.

- Odwrotność dodatku dla liczbą (*a*, *b*) jest (-*a*, -*b*) i multiplicative dla takiej liczby złożone z wyjątkiem (0, 0) jest

   (*a*/ (*a*<sup>2</sup> + *b*<sup>2</sup>), -*b*/ (*a*<sup>2</sup> + *b*<sup>2</sup>))

Przez reprezentujący liczbą *z* = (*a*, *b*) w formie *z* = *a*  +  *bi*, gdzie *i*<sup>2</sup> = -1, reguły dla algebraiczną zbioru liczb rzeczywistych można zastosować do zbioru liczb złożone i ich elementy. Na przykład:

   (1 + 2*i*) \* (2 + 3*i*)  
   = 1 \* (2 + 3*i*) + 2*i* \* (2 + 3*i*)  
   = (2 + 3*i*) + (4*i* + 6*i*<sup>2</sup>)  
   = (2 - 6) + (3 + 4)*i*  
   = -4 + 7*i*

Liczby złożone systemu jest polem, ale nie jest polem uporządkowane. Nie ma żadnych kolejności numerów złożone z powodu pola liczb rzeczywistych i jego podzbiorów, więc nierówności nie można zastosować do liczby złożone, ponieważ mają one liczb rzeczywistych.

Istnieją trzy często występującą formą reprezentujący liczbą *z*:

- Kartezjańskimi: *z* = *a* + *analizy biznesowej*

- Biegunowego: *z* = *r* (cos *p* + *i* sin *p*)

- Wykładnicza: *z* = *r* \* *e*<sup>*ip*</sup>

Terminów używanych w tych standardowe reprezentacje liczbą są określane w następujący sposób:

- Składnik rzeczywistym kartezjańskimi lub część rzeczywista *a*.

- Wyrażenie Liczba_zespolona kartezjańskimi składnika lub urojony części *b*.

- Modulo lub wartość bezwzględna liczby złożone *r*.

- Kąt argument lub faza *p* w radianach.

Inaczej, funkcji zwracających wiele wartości są musi zwrócić wartość główną dla ich argumentów większa niż - π i mniejsza niż lub równe + π, ich jednej wartości. Kąty wszystkie muszą być wyrażone w radianach, których koło istnieje radianach 2π (360 stopni).

### <a name="functions"></a>Funkcje

|Funkcja|Opis|
|-|-|
|[ABS](../standard-library/complex-functions.md#abs)|Oblicza resztę z liczbą.|
|[ARG](../standard-library/complex-functions.md#arg)|Wyodrębnia argument z liczbą.|
|[conj](../standard-library/complex-functions.md#conj)|Zwraca zespolonej liczbą.|
|[COS](../standard-library/complex-functions.md#cos)|Zwraca cosinus liczby złożonej.|
|[COSH](../standard-library/complex-functions.md#cosh)|Zwraca cosinus hiperboliczny dla liczby złożonej.|
|[EXP](../standard-library/complex-functions.md#exp)|Zwraca funkcja wykładnicza z liczbą.|
|[imag](../standard-library/complex-functions.md#imag)|Wyodrębnia urojony składnik liczbą.|
|[log](../standard-library/complex-functions.md#log)|Zwraca logarytm naturalny liczby złożonej.|
|[log10](../standard-library/complex-functions.md#log10)|Zwraca logarytm 10 liczbą.|
|[norm —](../standard-library/complex-functions.md#norm)|Wyodrębnia normy liczbą.|
|[polar](../standard-library/complex-functions.md#polar)|Zwraca liczby złożonej, co odpowiada określonym modulo i argumentu, w postaci kartezjańskimi.|
|[Pow](../standard-library/complex-functions.md#pow)|Oblicza liczby złożonej uzyskany przez zwiększenie base, która jest liczbą do potęgi równej innej liczbie złożone.|
|[rzeczywiste](../standard-library/complex-functions.md#real)|Wyodrębnia rzeczywistych składnik liczbą.|
|[SIN](../standard-library/complex-functions.md#sin)|Zwraca sinus liczby złożonej.|
|[SINH](../standard-library/complex-functions.md#sinh)|Zwraca sinus hiperboliczny liczby złożonej.|
|[sqrt](../standard-library/complex-functions.md#sqrt)|Zwraca pierwiastek kwadratowy z liczby złożonej.|
|[tan](../standard-library/complex-functions.md#tan)|Zwraca tangens liczby złożonej.|
|[TANH](../standard-library/complex-functions.md#tanh)|Zwraca tangens hiperboliczny dla liczby złożonej.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator!=](../standard-library/complex-operators.md#op_neq)|Testy pod kątem nierówności między dwie liczb zespolonych, jeden lub oba mogą należeć do podzbioru typ części rzeczywistych i urojony.|
|[operator *](../standard-library/complex-operators.md#op_star)|Mnoży dwie liczby złożone, przynajmniej jeden z nich może należeć do podzbioru typ części rzeczywistych i urojony.|
|[operator +](../standard-library/complex-operators.md#op_add)|Dodaje dwie liczb zespolonych, przynajmniej jeden z nich może należeć do podzbioru typ części rzeczywistych i urojony.|
|[operator-](../standard-library/complex-operators.md#operator-)|Odejmuje dwie liczby złożone, przynajmniej jeden z nich może należeć do podzbioru typ części rzeczywistych i urojony.|
|[operator /](../standard-library/complex-operators.md#op_div)|Dzieli dwie liczby złożone, przynajmniej jeden z nich może należeć do podzbioru typ części rzeczywistych i urojony.|
|[Operator <\<](../standard-library/complex-operators.md#op_lt_lt)|Funkcja szablonu, która wstawia liczby złożonej do strumienia wyjściowego.|
|[operator==](../standard-library/complex-operators.md#op_eq_eq)|Testy równości między dwie liczb zespolonych, jeden lub oba mogą należeć do podzbioru typ części rzeczywistych i urojony.|
|[operator>>](../standard-library/complex-operators.md#op_gt_gt)|Funkcja szablonu, który wyodrębnia złożona wartość ze strumienia wejściowego.|

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[złożone\<podwójne >](../standard-library/complex-double.md)|Klasa jawnie specjalne szablonu opisuje obiekt, który przechowuje uporządkowanej parę obiektów, zarówno typu **podwójne**, gdzie część rzeczywista liczbą reprezentuje pierwszy i drugi reprezentuje wyrażenie Liczba_zespolona część.|
|[złożone\<float >](../standard-library/complex-float.md)|Klasa jawnie specjalne szablonu opisuje obiekt, który przechowuje uporządkowanej parę obiektów, zarówno typu **float**, gdzie część rzeczywista liczbą reprezentuje pierwszy i drugi reprezentuje wyrażenie Liczba_zespolona część.|
|[złożone\<podwójnej długości >](../standard-library/complex-long-double.md)|Klasa jawnie specjalne szablonu opisuje obiekt, który przechowuje uporządkowanej parę obiektów, zarówno typu **podwójnej długości**, gdzie część rzeczywista liczbą reprezentuje pierwszy i drugi reprezentuje wyrażenie Liczba_zespolona część.|
|[complex](../standard-library/complex-class.md)|Klasa szablonu opisuje obiekt, który reprezentuje system liczby złożonej i wykonywanie operacji arytmetycznych złożonych.|

### <a name="literals"></a>Literały

\<Złożonych > nagłówka definiuje następujące [literały definiowane przez użytkownika](../cpp/user-defined-literals-cpp.md) którego Utwórz wiele złożone z rzeczywistego trwa zero i urojony część jest wartość parametru wejściowego.

|||
|-|-|
|`constexpr complex<long double> operator""il(long double d)`<br /><br /> `constexpr complex<long double> operator""il(unsigned long long d)`|Zwraca: `complex<long double>{0.0L, static_cast<long double>(d)}`|
|`constexpr complex<double> operator""i(long double d)`<br /><br /> `constexpr complex<double> operator""i(unsigned long long d)`|Zwraca: `complex<double>{0.0, static_cast<double>(d)}`.|
|`constexpr complex<float> operator""if(long double d)`<br /><br /> `constexpr complex<float> operator""if(unsigned long long d)`|Zwraca: `complex<float>{0.0f, static_cast<float>(d)}`.|

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
