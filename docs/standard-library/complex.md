---
title: '&lt;complex &gt;'
ms.date: 11/04/2016
f1_keywords:
- <complex>
- std::<complex>
helpviewer_keywords:
- complex header
ms.assetid: 5e728995-3059-496a-9ce9-61d1bfbe4f2b
ms.openlocfilehash: 071e9369cdd0469d8ddc1c6649a3801732d8e23f
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688220"
---
# <a name="ltcomplexgt"></a>&lt;complex &gt;

Definiuje szablon klasy kontenera `complex` i jego szablony pomocnicze.

## <a name="requirements"></a>Wymagania

**Nagłówek**: \<complex >

**Przestrzeń nazw:** std

## <a name="remarks"></a>Uwagi

Liczba zespolona to uporządkowana para liczb rzeczywistych. W warunkach czysto geometrycznych Płaszczyzna złożona to rzeczywista, dwuwymiarowa płaszczyzna. Specjalne cechy złożonej płaszczyzny, która odróżnia ją od rzeczywistej płaszczyzny, są spowodowane jej dodatkową strukturą algebraicznych. Ta struktura algebraicznych ma dwie podstawowe operacje:

- Dodanie zdefiniowane jako (*a*, *b*) + (*c*, *d*) = (*a*  + *c*, *b*  + *d*)

- Mnożenie zdefiniowane jako (*a*, *b*) \* (*c*, *d*) = (*AC*  - *BD*, *AD*  + *BC*)

Zestaw liczb zespolonych z operacjami złożonego dodawania i złożonego mnożenia jest polem w standardowym sensie algebraicznych:

- Operacje dodawania i mnożenia są komutatywnae i asocjacyjne i mnożenia są dystrybuowane z dodawaniem dokładnie tak samo, jak w przypadku rzeczywistego dodawania i mnożenia w polu liczby rzeczywiste.

- Liczba zespolona (0, 0) jest tożsamością dodatku i (1, 0) jest tożsamością mnożenia.

- Dodatek odwrotny dla liczby zespolonej (*a*, *b*) to (-*a*,-*b*) i mnożenia odwrotny dla wszystkich takich złożonych liczb, z wyjątkiem (0, 0) to

   (*a*/(*a/* <sup>2</sup>  + *b*<sup>2</sup>),-*b*/(*a*<sup>2</sup>  + *b*<sup>2</sup>))

Reprezentując liczbę zespoloną *z* = (*a*, *b*) w postaci *z* * =   + * *BI*, gdzie *i*<sup>2</sup> =-1, reguły dla algebry zestawu liczb rzeczywistych mogą być stosowane do zestawu złożonego liczby i ich składniki. Na przykład:

   (1 + 2*i*) \* (2 + 3*i*) = 1 \* (2 + 3*i*) + 2*i* \* (2 + 3*i*) = (2 + 3*i*) + (4*i* + 6*i*<sup>2</sup>) = (2-6) + (3 + 4)*i* =-4 + 7*i*

System liczb zespolonych to pole, ale nie jest to pole uporządkowane. Nie ma kolejności liczb zespolonych, ponieważ istnieją pola liczb rzeczywistych i ich podzestawy, dlatego nie można zastosować nierówności do liczb zespolonych, ponieważ są one liczbami rzeczywistymi.

Istnieją trzy popularne formy przedstawiające liczbę zespoloną *z*:

- Kartezjańskiego: *z*  =  * + * *BI*

- Biegunowy: *z*  = *r* (cos *p*  + *i* Sin *p*)

- Wykładniczy: *z*  = *r* \* *e*<sup>*IP*</sup>

Warunki użyte w tych standardowych reprezentacjach liczby zespolonej są określane w następujący sposób:

- Prawdziwy składnik kartezjańskiego lub część rzeczywista *a*.

- Składnik kartezjańskiego urojony lub część urojona *b*.

- Moduł lub wartość bezwzględna liczby zespolonej *r*.

- Kąt argumentu lub fazy *p* w radianach.

O ile nie określono inaczej, funkcje, które mogą zwracać wiele wartości, są wymagane do zwrócenia wartości głównej dla argumentów większej niż-π i mniejszej lub równej + π, aby zachować je pojedynczą wartość. Wszystkie kąty muszą być wyrażone w radianach, gdzie 2π radianów (360 stopni) w okręgu.

## <a name="members"></a>Elementy członkowskie

### <a name="functions"></a>Funkcje

|||
|-|-|
|[ABS](../standard-library/complex-functions.md#abs)|Oblicza moduł liczby zespolonej.|
|[Acos](../standard-library/complex-functions.md#acos)||
|[ACOSH —](../standard-library/complex-functions.md#acosh)||
|[ARG](../standard-library/complex-functions.md#arg)|Wyodrębnia argument z liczby zespolonej.|
|[Asin](../standard-library/complex-functions.md#asin)||
|[ASINH —](../standard-library/complex-functions.md#asinh)||
|[atan](../standard-library/complex-functions.md#atan)||
|[ATANH —](../standard-library/complex-functions.md#atanh)||
|[conj](../standard-library/complex-functions.md#conj)|Zwraca zespoloną wartość sprzężoną liczby zespolonej.|
|[cosinus](../standard-library/complex-functions.md#cos)|Zwraca cosinus liczby zespolonej.|
|[cosh —](../standard-library/complex-functions.md#cosh)|Zwraca cosinus hiperboliczny liczby zespolonej.|
|[EXP](../standard-library/complex-functions.md#exp)|Zwraca funkcję wykładniczą liczby zespolonej.|
|[imag](../standard-library/complex-functions.md#imag)|Wyodrębnia część urojoną liczby zespolonej.|
|[rejestrowane](../standard-library/complex-functions.md#log)|Zwraca logarytm naturalny liczby zespolonej.|
|[log10 —](../standard-library/complex-functions.md#log10)|Zwraca logarytm dziesiętny liczby zespolonej.|
|[oblicza](../standard-library/complex-functions.md#norm)|Wyodrębnia normę liczby zespolonej.|
|[Wykres](../standard-library/complex-functions.md#polar)|Zwraca liczbę zespoloną, która odnosi się do określonego modułu i argumentu w formie kartezjańskiego.|
|[pow](../standard-library/complex-functions.md#pow)|Oblicza liczbę zespoloną uzyskaną przez podnoszenie wartości bazowej, która jest liczbą zespoloną do potęgi innej liczby zespolonej.|
|[proj](../standard-library/complex-functions.md#proj)||
|[czasie rzeczywistym](../standard-library/complex-functions.md#real)|Wyodrębnia prawdziwy składnik liczby zespolonej.|
|[sinus](../standard-library/complex-functions.md#sin)|Zwraca sinus liczby zespolonej.|
|[SINH](../standard-library/complex-functions.md#sinh)|Zwraca sinus hiperboliczny liczby zespolonej.|
|[sqrt](../standard-library/complex-functions.md#sqrt)|Zwraca pierwiastek kwadratowy z liczby zespolonej.|
|[Tan](../standard-library/complex-functions.md#tan)|Zwraca tangens liczby zespolonej.|
|[TANH —](../standard-library/complex-functions.md#tanh)|Zwraca tangens hiperboliczny liczby zespolonej.|

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator!=](../standard-library/complex-operators.md#op_neq)|Testuje pod kątem nierówności między dwoma złożonymi liczbami, jedną lub obie, które mogą należeć do podzbioru typu dla części rzeczywistych i urojonych.|
|[zakład](../standard-library/complex-operators.md#op_star)|Mnoży dwie liczby zespolone, jedno lub oba, które mogą należeć do podzbioru typu dla części rzeczywistych i urojonych.|
|[operator +](../standard-library/complex-operators.md#op_add)|Dodaje dwie liczby zespolone, jedno lub oba, które mogą należeć do podzbioru typu dla części rzeczywistych i urojonych.|
|[zakład](../standard-library/complex-operators.md#operator-)|Odejmuje dwie liczby zespolone, jedno lub oba, które mogą należeć do podzbioru typu dla części rzeczywistych i urojonych.|
|[zakład](../standard-library/complex-operators.md#op_div)|Dzieli dwie liczby zespolone, jedno lub oba, które mogą należeć do podzbioru typu dla części rzeczywistych i urojonych.|
|[< operatora \<](../standard-library/complex-operators.md#op_lt_lt)|Funkcja szablonu, która wstawia liczbę zespoloną do strumienia wyjściowego.|
|[operator = =](../standard-library/complex-operators.md#op_eq_eq)|Testuje równość między dwoma złożonymi liczbami, jedno lub oba, które mogą należeć do podzbioru typu dla części rzeczywistych i urojonych.|
|[> operatora >](../standard-library/complex-operators.md#op_gt_gt)|Funkcja szablonu, która wyodrębnia wartość złożoną ze strumienia wejściowego.|

### <a name="classes"></a>Klasy

|||
|-|-|
|[złożone > \<double](../standard-library/complex-double.md)|Jawnie wyspecjalizowany szablon klasy opisuje obiekt, który przechowuje uporządkowaną parę obiektów, obie typu **Double**, gdzie pierwsza reprezentuje rzeczywistą część liczby zespolonej, a druga reprezentuje część urojoną.|
|[złożone > \<float](../standard-library/complex-float.md)|Jawnie wyspecjalizowany szablon klasy opisuje obiekt, który przechowuje uporządkowaną parę obiektów, obu typów **zmiennoprzecinkowych**, gdzie pierwsza reprezentuje rzeczywistą część liczby zespolonej, a druga reprezentuje część urojoną.|
|[złożone \<long podwójne >](../standard-library/complex-long-double.md)|Jawnie wyspecjalizowany szablon klasy opisuje obiekt, który przechowuje uporządkowaną parę obiektów, obie typu **Long Double**, gdzie pierwsza reprezentuje rzeczywistą część liczby zespolonej, a druga reprezentuje część urojoną.|
|[złożonych](../standard-library/complex-class.md)|Szablon klasy opisuje obiekt używany do reprezentowania kompleksowego systemu liczb i wykonywania złożonych operacji arytmetycznych.|

### <a name="literals"></a>Literały

Nagłówek \<complex > definiuje następujące [literały zdefiniowane przez użytkownika](../cpp/user-defined-literals-cpp.md) , które tworzą liczbę zespoloną z zerem częścią rzeczywistą i części urojoną wartości parametru wejściowego.

|||
|-|-|
|`constexpr complex<long double> operator""il(long double d)`<br />`constexpr complex<long double> operator""il(unsigned long long d)`|Zwraca: `complex<long double>{0.0L, static_cast<long double>(d)}`|
|`constexpr complex<double> operator""i(long double d)`<br />`constexpr complex<double> operator""i(unsigned long long d)`|Zwraca: `complex<double>{0.0, static_cast<double>(d)}`.|
|`constexpr complex<float> operator""if(long double d)`<br />`constexpr complex<float> operator""if(unsigned long long d)`|Zwraca: `complex<float>{0.0f, static_cast<float>(d)}`.|

## <a name="see-also"></a>Zobacz także

[Odwołania do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md) \
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
