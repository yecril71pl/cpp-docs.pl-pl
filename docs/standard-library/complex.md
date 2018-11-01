---
title: '&lt;complex&gt;'
ms.date: 11/04/2016
f1_keywords:
- <complex>
- std::<complex>
helpviewer_keywords:
- complex header
ms.assetid: 5e728995-3059-496a-9ce9-61d1bfbe4f2b
ms.openlocfilehash: afcdb1246d9c02f83dbc8708326d10e802ad2779
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50525869"
---
# <a name="ltcomplexgt"></a>&lt;complex&gt;

Definiuje klasę szablonu pojemnika `complex` i jego szablonów pomocniczych.

## <a name="syntax"></a>Składnia

```cpp
#include <complex>
```

## <a name="remarks"></a>Uwagi

Liczby zespolonej jest uporządkowana para liczb rzeczywistych. W warunkach czysto geometryczne płaszczyzna złożone jest prawdziwe, dwuwymiarowy płaszczyzny. Specjalne właściwości płaszczyzny złożone, które odróżnia go od rzeczywistego płaszczyzny są spowodowane przez o dodatkowe algebraicznych struktury. Ta struktura algebraicznych ma dwie podstawowe operacje:

- Dodanie zdefiniowany jako (*a*, *b*) + (*c*, *d*) = (*a* + *c* , *b* + *d*)

- Zdefiniowany jako mnożenia (*a*, *b*) \* (*c*, *d*) = (*ac*  -  *bd*, *ad* + *bc*)

Zestaw liczby zespolone z operacjami złożonych Dodawanie i mnożenie złożone są z polem w standardowym sensie algebraicznych:

- Operacje Dodawanie i mnożenie to przemiennego i asocjacyjnych i mnożenia dystrybuuje przez dodanie dokładnie tak jak w przypadku rzeczywistych Dodawanie i mnożenie pola liczb rzeczywistych.

- Liczby zespolonej (0, 0) jest tożsamość dodatku i (1, 0) mnożenia tożsamości.

- Odwrotność dodatku dla liczbą (*a*, *b*) jest (-*a*, -*b*) i multiplicative dla takiej liczby złożone z wyjątkiem (0, 0) jest

   (*a*/ (*a*<sup>2</sup> + *b*<sup>2</sup>), -*b*/ (*a*<sup>2</sup> + *b*<sup>2</sup>))

Przez reprezentujący liczbą *z* = (*a*, *b*) w formie *z* = *a*  +  *bi*, gdzie *i*<sup>2</sup> = -1, reguły dla algebraiczną zbioru liczb rzeczywistych można zastosować do zbioru liczb złożone i ich elementy. Na przykład:

   (1 + 2*i*) \* (2 + 3*i*) = 1 \* (2 + 3*i*) + 2*i* \* (2 + 3*i*) = (2 + 3*i*) + (4*i* + 6*i*<sup>2</sup>) = (2-6) + (3 i 4)*i* = -4 + 7*i*

System liczby zespolone jest polem, ale nie jest polem uporządkowany. Nie ma, nie porządkowanie liczby zespolone, ponieważ ma pola liczb rzeczywistych i jego podzestawy tak nierówności nie można zastosować do liczby zespolone, ponieważ są one na liczby rzeczywiste.

Istnieją trzy typowe rodzaje reprezentujący liczby zespolonej *z*:

- Kartezjańskimi: *z* = *a* + *analizy biznesowej*

- Biegunowego: *z* = *r* (cos *p* + *i* sin *p*)

- Wartość wykładnicza: *z* = *r* \* *e*<sup>*adresu ip*</sup>

Terminy używane w tych standardowych reprezentacje liczby zespolonej są określane w następujący sposób:

- Składnik rzeczywistym kartezjańskimi lub część rzeczywista *a*.

- Urojone części Kartezjańskiego lub urojone części *b*.

- Modulo lub wartość bezwzględną liczby zespolonej *r*.

- Kąt argument lub fazy *p* w radianach.

Chyba że określono inaczej, funkcji, które mogą zwrócić wiele wartości są wymagane w celu zwrócenia wartości podmiotu zabezpieczeń dla swoich argumentów, większa niż - π i mniejsza niż lub równe + π, zachować je w pojedynczej wartości. Wszystkie kąty musi być wyrażony w radianach, których 2π radianów (360 stopni) znajduje się w okręgu.

### <a name="functions"></a>Funkcje

|Funkcja|Opis|
|-|-|
|[ABS](../standard-library/complex-functions.md#abs)|Oblicza resztę z liczbą.|
|[ARG](../standard-library/complex-functions.md#arg)|Wyodrębnia argumentu z liczbą.|
|[conj](../standard-library/complex-functions.md#conj)|Zwraca zespolonej liczbą.|
|[COS](../standard-library/complex-functions.md#cos)|Zwraca cosinus liczby zespolonej.|
|[COSH](../standard-library/complex-functions.md#cosh)|Zwraca cosinus hiperboliczny liczby zespolonej.|
|[EXP](../standard-library/complex-functions.md#exp)|Zwraca wartość funkcji wykładniczej liczby zespolonej.|
|[imag](../standard-library/complex-functions.md#imag)|Wyodrębnia urojone części liczby zespolonej.|
|[log](../standard-library/complex-functions.md#log)|Zwraca logarytm naturalny liczby zespolonej.|
|[log10](../standard-library/complex-functions.md#log10)|Zwraca logarytm 10 liczbą.|
|[norm](../standard-library/complex-functions.md#norm)|Wyodrębnia normy liczbą.|
|[polar](../standard-library/complex-functions.md#polar)|Zwraca liczby zespolonej, odnoszące się do określonego modułu, a argument w postaci kartezjańskich wizualizacji.|
|[Pow](../standard-library/complex-functions.md#pow)|Oblicza liczby zespolonej uzyskać, tworząc podstawowy, która jest liczbą do potęgi innej liczby zespolonej.|
|[rzeczywiste](../standard-library/complex-functions.md#real)|Wyodrębnia rzeczywisty składnik liczby zespolonej.|
|[SIN](../standard-library/complex-functions.md#sin)|Zwraca sinus liczby zespolonej.|
|[SINH](../standard-library/complex-functions.md#sinh)|Zwraca sinus hiperboliczny liczby zespolonej.|
|[sqrt](../standard-library/complex-functions.md#sqrt)|Zwraca pierwiastek kwadratowy liczby zespolonej.|
|[tan](../standard-library/complex-functions.md#tan)|Zwraca tangens liczby zespolonej.|
|[TANH](../standard-library/complex-functions.md#tanh)|Zwraca tangens hiperboliczny liczby zespolonej.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator!=](../standard-library/complex-operators.md#op_neq)|Testuje pod kątem nierówności pomiędzy dwóch liczb zespolonych, jednego lub obu z nich mogą należeć do podzbioru typu rzeczywiste i urojone części.|
|[operator *](../standard-library/complex-operators.md#op_star)|Mnoży dwie liczby zespolone, jednego lub obu z nich może należeć do podzbioru typu rzeczywiste i urojone części.|
|[operator +](../standard-library/complex-operators.md#op_add)|Dodaje dwie liczby zespolone, jeden lub oba może należeć do podzbioru typu rzeczywiste i urojone części.|
|[operator-](../standard-library/complex-operators.md#operator-)|Odejmuje dwie liczby zespolone, jednego lub obu z nich może należeć do podzbioru typu rzeczywiste i urojone części.|
|[operator /](../standard-library/complex-operators.md#op_div)|Dzieli dwie liczby zespolone, jednego lub obu z nich mogą należeć do podzbioru typu rzeczywiste i urojone części.|
|[Operator <\<](../standard-library/complex-operators.md#op_lt_lt)|Funkcja szablonu, który wstawia liczby zespolonej do strumienia wyjściowego.|
|[operator==](../standard-library/complex-operators.md#op_eq_eq)|Testuje pod kątem równości pomiędzy dwóch liczb zespolonych, jednego lub obu z nich mogą należeć do podzbioru typu rzeczywiste i urojone części.|
|[operator>>](../standard-library/complex-operators.md#op_gt_gt)|Funkcja szablonu, która wyodrębnia wartość złożoną ze strumienia wejściowego.|

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[złożone\<double >](../standard-library/complex-double.md)|Klasa jawnie wyspecjalizowane szablonu opisuje obiekt przechowujący uporządkowana para obiektów, oba typu **double**, gdzie pierwszy reprezentuje część rzeczywista liczby zespolonej, a druga urojone części.|
|[złożone\<float >](../standard-library/complex-float.md)|Klasa jawnie wyspecjalizowane szablonu opisuje obiekt przechowujący uporządkowana para obiektów, oba typu **float**, gdzie pierwszy reprezentuje część rzeczywista liczby zespolonej, a druga urojone części.|
|[złożone\<typu long double >](../standard-library/complex-long-double.md)|Klasa jawnie wyspecjalizowane szablonu opisuje obiekt przechowujący uporządkowana para obiektów, oba typu **typu long double**, gdzie pierwszy reprezentuje część rzeczywista liczby zespolonej, a druga urojone części.|
|[complex](../standard-library/complex-class.md)|Klasa szablonu opisuje obiekt używany do reprezentowania liczby zespolonej systemu i wykonywać złożone operacje arytmetyczne.|

### <a name="literals"></a>Literały

\<Złożonych > nagłówka definiuje następujące [literały definiowane przez użytkownika](../cpp/user-defined-literals-cpp.md) którego tworzenie liczby zespolonej przy użyciu rzeczywistego trwa zero i urojone część jest wartość parametru wejściowego.

|||
|-|-|
|`constexpr complex<long double> operator""il(long double d)`<br /><br /> `constexpr complex<long double> operator""il(unsigned long long d)`|Zwraca: `complex<long double>{0.0L, static_cast<long double>(d)}`|
|`constexpr complex<double> operator""i(long double d)`<br /><br /> `constexpr complex<double> operator""i(unsigned long long d)`|Zwraca: `complex<double>{0.0, static_cast<double>(d)}`.|
|`constexpr complex<float> operator""if(long double d)`<br /><br /> `constexpr complex<float> operator""if(unsigned long long d)`|Zwraca: `complex<float>{0.0f, static_cast<float>(d)}`.|

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
