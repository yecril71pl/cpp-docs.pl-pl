---
title: discrete_distribution — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- random/std::discrete_distribution
- random/std::discrete_distribution::reset
- random/std::discrete_distribution::probabilities
- random/std::discrete_distribution::param
- random/std::discrete_distribution::min
- random/std::discrete_distribution::max
- random/std::discrete_distribution::operator()
- random/std::discrete_distribution::param_type
- random/std::discrete_distribution::param_type::probabilities
- random/std::discrete_distribution::param_type::operator==
- random/std::discrete_distribution::param_type::operator!=
dev_langs:
- C++
helpviewer_keywords:
- std::discrete_distribution [C++]
- std::discrete_distribution [C++], reset
- std::discrete_distribution [C++], probabilities
- std::discrete_distribution [C++], param
- std::discrete_distribution [C++], min
- std::discrete_distribution [C++], max
- std::discrete_distribution [C++], param_type
- std::discrete_distribution [C++], param_type
ms.assetid: 8c8ba8f8-c06f-4f07-b354-f53950142fcf
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 676de6dcbb11ea6451d845c8ac357fc498958c88
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="discretedistribution-class"></a>discrete_distribution — Klasa

Generuje dystrybucji odrębny liczba całkowita, którą ma szerokość uniform odstępach czasu uniform prawdopodobieństwo w każdym interwale.

## <a name="syntax"></a>Składnia

```cpp
template<class IntType = int>
class discrete_distribution
   {
public:
   // types
   typedef IntType result_type;
   struct param_type;

   // constructor and reset functions
   discrete_distribution();
   template <class InputIterator>
   discrete_distribution(InputIterator firstW, InputIterator lastW);
   discrete_distribution(initializer_list<double> weightlist);
   template <class UnaryOperation>
   discrete_distribution(size_t count, double xmin, double xmax, UnaryOperation funcweight);
   explicit discrete_distribution(const param_type& parm);
   void reset();

   // generating functions
   template <class URNG>
   result_type operator()(URNG& gen);
   template <class URNG>
   result_type operator()(URNG& gen, const param_type& parm);

   // property functions
   vector<double> probabilities() const;
   param_type param() const;
   void param(const param_type& parm);
   result_type min() const;
   result_type max() const;
   };
```

### <a name="parameters"></a>Parametry

*IntType* domyślnie integer — typ wyniku `int`. Dla typów możliwych [ \<losowe >](../standard-library/random.md).

## <a name="remarks"></a>Uwagi

Tej dystrybucji próbkowania ma szerokość uniform odstępach czasu uniform prawdopodobieństwo w każdym interwale. Uzyskać informacji o innych dystrybucje próbkowania, zobacz [piecewise_linear_distribution — klasa](../standard-library/piecewise-linear-distribution-class.md) i [piecewise_constant_distribution — klasa](../standard-library/piecewise-constant-distribution-class.md).

Poniższe łącza tabeli do artykułów na temat poszczególnych członków:

|||
|-|-|
|[discrete_distribution](#discrete_distribution)|`discrete_distribution::param`|
|`discrete_distribution::operator()`|[param_type](#param_type)|

Funkcja właściwości `vector<double> probabilities()` zwraca poszczególnych prawdopodobieństwa dla każdego całkowitą wygenerowany.

Aby uzyskać więcej informacji o dystrybucji klasy i ich elementy członkowskie, zobacz [ \<losowe >](../standard-library/random.md).

## <a name="example"></a>Przykład

```cpp
// compile with: /EHsc /W4
#include <random>
#include <iostream>
#include <iomanip>
#include <string>
#include <map>

using namespace std;

void test(const int s) {

    // uncomment to use a non-deterministic generator
    // random_device rd;
    // mt19937 gen(rd());
    mt19937 gen(1701);

    discrete_distribution<> distr({ 1, 2, 3, 4, 5 });

    cout << endl;
    cout << "min() == " << distr.min() << endl;
    cout << "max() == " << distr.max() << endl;
    cout << "probabilities (value: probability):" << endl;
    vector<double> p = distr.probabilities();
    int counter = 0;
    for (const auto& n : p) {
        cout << fixed << setw(11) << counter << ": " << setw(14) << setprecision(10) << n << endl;
        ++counter;
    }
    cout << endl;

    // generate the distribution as a histogram
    map<int, int> histogram;
    for (int i = 0; i < s; ++i) {
        ++histogram[distr(gen)];
    }

    // print results
    cout << "Distribution for " << s << " samples:" << endl;
    for (const auto& elem : histogram) {
        cout << setw(5) << elem.first << ' ' << string(elem.second, ':') << endl;
    }
    cout << endl;
}

int main()
{
    int samples = 100;

    cout << "Use CTRL-Z to bypass data entry and run using default values." << endl;
    cout << "Enter an integer value for the sample count: ";
    cin >> samples;

    test(samples);
}
```

```Output
Use CTRL-Z to bypass data entry and run using default values.
Enter an integer value for the sample count: 100
min() == 0
max() == 4
probabilities (value: probability):
          0:   0.0666666667
          1:   0.1333333333
          2:   0.2000000000
          3:   0.2666666667
          4:   0.3333333333

Distribution for 100 samples:
    0 :::
    1 ::::::::::::::
    2 ::::::::::::::::::
    3 :::::::::::::::::::::::::::::
    4 ::::::::::::::::::::::::::::::::::::
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<losowe >

**Namespace:** Standard

## <a name="discrete_distribution"></a>  discrete_distribution::discrete_distribution

Tworzy dystrybucji.

```cpp
// default constructor
discrete_distribution();

// construct using a range of weights, [firstW, lastW)
template <class InputIterator>
discrete_distribution(InputIterator firstW, InputIterator lastW);

// construct using an initializer list for range of weights
discrete_distribution(initializer_list<double> weightlist);

// construct using unary operation function
template <class UnaryOperation>
discrete_distribution(size_t count, double low, double high, UnaryOperation weightfunc);

// construct from an existing param_type structure
explicit discrete_distribution(const param_type& parm);
```

### <a name="parameters"></a>Parametry

*firstW* pierwszy iteratora na liście, z którego można utworzyć dystrybucji.

*lastW* ostatniego iteratora na liście, z którego można utworzyć dystrybucji (z systemem innym niż inclusive ponieważ Iteratory użyj pustego elementu dla elementu end).

*weightlist* [initializer_list](../cpp/initializers.md) z którego można utworzyć dystrybucji.

*Liczba* liczba elementów w zakresie dystrybucji. Jeśli `count==0`, równoważne konstruktora domyślnego (zawsze generuje zero).

*niski* najniższa wartość z zakresu dystrybucji.

*Wysoka* najwyższą wartość z zakresu dystrybucji.

*weightfunc* obiekt reprezentujący prawdopodobieństwa rozkładu. Zarówno parametr i zwracana wartość musi być możliwe do przekonwertowania na `double`.

*Parametr* `param_type` struktury użyta do skonstruowania dystrybucji.

### <a name="remarks"></a>Uwagi

Domyślny konstruktor konstrukcji obiektu, którego wartość prawdopodobieństwa przechowywanych ma jeden element o wartości 1. Spowoduje to dystrybucji, który zawsze generuje wartość zero.

Konstruktor zakresu iteratora, który ma następujące parametry *firstW* i *lastW* tworzy obiekt dystrybucji przy użyciu wartości wagi przejęty sekwencji interwału od Iteratory [ *firstW*, *lastW*).

Konstruktor listy inicjatorów, który ma *weightlist* parametru tworzy obiekt dystrybucji o wagach na liście inicjatora *weightlist*.

Konstruktor, który ma *liczba*, *niski*, *wysokiej*, i *weightfunc* na podstawie parametrów konstrukcje zainicjować obiektu dystrybucji te reguły:

- Jeśli *liczba* < 1, **n** = 1 i jako taki jest odpowiednikiem domyślnego konstruktora generowania zawsze zero.
- Jeśli *liczba* > 0, **n** = *liczba*. Podany **d** = (*wysokiej* - *niski*) / **n** jest większa niż zero, przy użyciu **d** uniform podzakresy, każdy wagi jest przypisana w następujący sposób: `weight[k] = weightfunc(x)`, gdzie **x** = *niski* + **k**  *  **d** + **d** / 2 do **k** = 0,..., **n** - 1.

Konstruktor, który ma `param_type` parametru *parametrów* tworzy obiekt dystrybucji przy użyciu *parametr* jako struktura przechowywanego parametru.

## <a name="param_type"></a>  discrete_distribution::param_type

Przechowuje wszystkie parametry dystrybucji.

```cpp
struct param_type {
   typedef discrete_distribution<result_type> distribution_type;
   param_type();

   // construct using a range of weights, [firstW, lastW)
   template <class InputIterator>
   param_type(InputIterator firstW, InputIterator lastW);

   // construct using an initializer list for range of weights
   param_type(initializer_list<double> weightlist);

   // construct using unary operation function
   template <class UnaryOperation>
   param_type(size_t count, double low, double high, UnaryOperation weightfunc);

   std::vector<double> probabilities() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };
```

### <a name="parameters"></a>Parametry

*firstW* pierwszy iteratora na liście, z którego można utworzyć dystrybucji.

*lastW* ostatniego iteratora na liście, z którego można utworzyć dystrybucji (z systemem innym niż inclusive ponieważ Iteratory użyj pustego elementu dla elementu end).

*weightlist* [initializer_list](../cpp/initializers.md) z którego można utworzyć dystrybucji.

*Liczba* liczba elementów w zakresie dystrybucji. Jeśli *liczba* wynosi 0, co jest równoważne konstruktora domyślnego (zawsze generuje zero).

*niski* najniższa wartość z zakresu dystrybucji.

*Wysoka* najwyższą wartość z zakresu dystrybucji.

*weightfunc* obiekt reprezentujący prawdopodobieństwa rozkładu. Zarówno parametr i zwracana wartość musi być możliwe do przekonwertowania na `double`.

*prawy* `param_type` obiekt do porównania z tym.

### <a name="remarks"></a>Uwagi

Ten pakiet parametrów mogą zostać przekazane do `operator()` do generowania wartości zwracanej.

## <a name="see-also"></a>Zobacz także

[\<losowe >](../standard-library/random.md)<br/>
