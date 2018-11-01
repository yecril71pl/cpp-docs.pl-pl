---
title: random_device — Klasa
ms.date: 11/04/2016
f1_keywords:
- random/std::random_device
- random/std::random_device::min
- random/std::random_device::max
- random/std::random_device::entropy
- random/std::random_device::operator()
helpviewer_keywords:
- std::random_device [C++]
- std::random_device [C++], min
- std::random_device [C++], max
- std::random_device [C++], entropy
- std::random_device [C++], entropy
ms.assetid: 4393d515-0cb6-4e0d-a2ba-c780f05dc1bf
ms.openlocfilehash: 783b8f587094c6d603cc02f41b516ebd7b1e9a08
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50580651"
---
# <a name="randomdevice-class"></a>random_device — Klasa

Generuje losową sekwencję z zewnętrznego urządzenia.

## <a name="syntax"></a>Składnia

```cpp
class random_device {
public:
   typedef unsigned int result_type;

   // constructor
   explicit random_device(const std::string& token = "");

   // properties
   static result_type min();
   static result_type max();
   double entropy() const;

   // generate
   result_type operator()();

   // no-copy functions
   random_device(const random_device&) = delete;
   void operator=(const random_device&) = delete;
   };
```

## <a name="members"></a>Elementy członkowskie

|||
|-|-|
|[random_device —](#random_device)|[entropy](#entropy)|
|[random_device::operator()](#op_call)||

## <a name="remarks"></a>Uwagi

Klasa opisuje źródła liczb losowych i jest dozwolone, ale nie muszą być niedeterministyczne i kryptograficznie bezpieczne według standardu ISO C++. W programie Visual Studio implementacji wartości utworzone są niedeterministyczne i kryptograficznie bezpieczne, ale działa wolniej niż generatorów utworzone na podstawie aparatów i adapterów aparatu (takie jak [mersenne_twister_engine —](../standard-library/mersenne-twister-engine-class.md), wysokiej jakości i szybkie aparatu wybór w przypadku większości aplikacji).

`random_device` wyniki są równomiernie rozłożone w zamkniętym zakresie [ `0, 2` <sup>32</sup>).

`random_device` nie ma żadnej gwarancji spowodować wywołanie bez blokowania.

Ogólnie rzecz biorąc `random_device` jest używany do generowania innych generatorów utworzone za pomocą aparatów lub adapterów aparatu. Aby uzyskać więcej informacji, zobacz [ \<losowy >](../standard-library/random.md).

## <a name="example"></a>Przykład

Poniższy kod przedstawia podstawowe funkcje tej klasy i przykłady wyników. Ze względu na charakter niedeterministyczne `random_device`, losowych wartości widocznych na **dane wyjściowe** sekcji nie będą zgodne wyniki. Jest to normalne i oczekiwane.

```cpp
// random_device_engine.cpp
// cl.exe /W4 /nologo /EHsc /MTd
#include <random>
#include <iostream>
using namespace std;

int main()
{
    random_device gen;

    cout << "entropy == " << gen.entropy() << endl;
    cout << "min == " << gen.min() << endl;
    cout << "max == " << gen.max() << endl;

    cout << "a random value == " << gen() << endl;
    cout << "a random value == " << gen() << endl;
    cout << "a random value == " << gen() << endl;
}
```

```Output
entropy == 32
min == 0
max == 4294967295
a random value == 2378414971
a random value == 3633694716
a random value == 213725214
```

W tym przykładzie jest uproszczony i nie językiem ogólne przypadek użycia dla tego generatora. Dla bardziej reprezentatywny przykładu kodu zobacz [ \<losowy >](../standard-library/random.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<losowy >

**Namespace:** standardowe

## <a name="random_device"></a>  random_device::random_device

Tworzy generator.

```cpp
random_device(const std::string& = "");
```

### <a name="remarks"></a>Uwagi

Konstruktor inicjuje generator, stosownie do potrzeb, ignorując parametr typu ciąg. Zwraca wartość typu zdefiniowanego w implementacji pochodną [wyjątek](../standard-library/exception-class.md) Jeśli `random_device` nie można zainicjować.

## <a name="entropy"></a>  random_device::Entropy

Oszacowuje losowość źródła.

```cpp
double entropy() const noexcept;
```

### <a name="remarks"></a>Uwagi

Element członkowski funkcji zwraca oszacowanie losowości źródła, mierzone w bitach.

## <a name="op_call"></a>  random_device::operator()

Zwraca wartość losową.

```cpp
result_type operator()();
```

### <a name="remarks"></a>Uwagi

Zwraca wartości równomiernie rozłożone w zamkniętym przedziale [ `min, max`] zgodnie z ustaleniami funkcji elementów członkowskich `min()` i `max()`. Zwraca wartość typu zdefiniowanego w implementacji pochodną [wyjątek](../standard-library/exception-class.md) Jeśli nie można uzyskać liczbę losową.

## <a name="see-also"></a>Zobacz także

[\<losowy >](../standard-library/random.md)<br/>
