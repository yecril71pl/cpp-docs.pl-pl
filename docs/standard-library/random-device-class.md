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
ms.openlocfilehash: 396f172d6a7f9fed72e19917a528f561d0110470
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320272"
---
# <a name="random_device-class"></a>random_device — Klasa

Generuje losową sekwencję z urządzenia zewnętrznego.

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
|[random_device](#random_device)|[entropy](#entropy)|
|[random_device::operator()](#op_call)||

## <a name="remarks"></a>Uwagi

Klasa opisuje źródło liczb losowych i jest dozwolone, ale nie musi być niedeterministyczne lub kryptograficznie bezpieczne przez standard ISO C++. W implementacji programu Visual Studio produkowane wartości są niedeterministyczne i kryptograficznie bezpieczne, ale działają wolniej niż generatory utworzone z aparatów i adapterów aparatu (takich jak [mersenne_twister_engine](../standard-library/mersenne-twister-engine-class.md), wysokiej jakości i szybki aparat wyboru dla większości aplikacji).

`random_device`wyniki są równomiernie rozłożone w `0, 2`zakresie zamkniętym [ <sup>32</sup>).

`random_device`nie gwarantuje, że spowoduje to połączenie bez blokowania.

Ogólnie rzecz `random_device` biorąc, jest używany do nasion innych generatorów utworzonych za pomocą silników lub adapterów silnika. Aby uzyskać więcej informacji, zobacz [ \<losowe>](../standard-library/random.md).

## <a name="example"></a>Przykład

Poniższy kod pokazuje podstawowe funkcje tej klasy i przykładowe wyniki. Ze względu na niedeterministyczny charakter `random_device`, losowe wartości pokazane w sekcji Dane **wyjściowe** nie będą zgodne z wynikami. Jest to normalne i oczekiwane.

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

Ten przykład jest uproszczony i nie jest reprezentatywny dla ogólnego przypadku użycia dla tego generatora. Aby uzyskać bardziej reprezentatywny przykład kodu, zobacz [ \<losowe>](../standard-library/random.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<losowe>

**Przestrzeń nazw:** std

## <a name="random_devicerandom_device"></a><a name="random_device"></a>random_device::random_device

Konstruuje generator.

```cpp
random_device(const std::string& = "");
```

### <a name="remarks"></a>Uwagi

Konstruktor inicjuje generator w razie potrzeby, ignorując parametr string. Zgłasza wartość typu zdefiniowanego przez implementację pochodną `random_device` [wyjątku,](../standard-library/exception-class.md) jeśli nie można zainicjować.

## <a name="random_deviceentropy"></a><a name="entropy"></a>random_device::entropia

Szacuje losowość źródła.

```cpp
double entropy() const noexcept;
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca oszacowanie losowości źródła, mierzone w bitach.

## <a name="random_deviceoperator"></a><a name="op_call"></a>random_device::operator()

Zwraca wartość losową.

```cpp
result_type operator()();
```

### <a name="remarks"></a>Uwagi

Zwraca wartości równomiernie rozłożone w `min, max`zamkniętym przedziale `min()` [ `max()`] określone przez funkcje członkowskie i . Zgłasza wartość typu zdefiniowanego przez implementację pochodną [wyjątku,](../standard-library/exception-class.md) jeśli nie można uzyskać liczby losowej.

## <a name="see-also"></a>Zobacz też

[\<losowe>](../standard-library/random.md)
