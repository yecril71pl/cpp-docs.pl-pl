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
ms.openlocfilehash: b2176ce7dcdefdcf4fc0846cd18b1b01d4de2916
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88843550"
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

[random_device](#random_device)\
[entropii](#entropy)\
[random_device:: operator ()](#op_call)

## <a name="remarks"></a>Uwagi

Klasa opisuje źródło liczb losowych i jest dozwolony, ale nie musi być deterministyczna lub kryptograficznie zabezpieczona przez standard ISO C++. W implementacji programu Visual Studio podane wartości są niedeterministyczne i kryptograficznie zabezpieczone, ale działają wolniej niż generatory utworzone za pomocą aparatów i adapterów silnikowych (takich jak [mersenne_twister_engine](../standard-library/mersenne-twister-engine-class.md), wysoka jakość i szybki wybór dla większości aplikacji).

`random_device`wyniki są równomiernie dystrybuowane w zamkniętym zakresie [ `0, 2` <sup>32</sup>).

`random_device` nie gwarantuje wyniku wywołania nieblokującego.

Ogólnie rzecz biorąc, `random_device` jest używany do wypełniania innych generatorów utworzonych za pomocą aparatów lub adapterów silników. Aby uzyskać więcej informacji, zobacz [\<random>](../standard-library/random.md).

## <a name="example"></a>Przykład

Poniższy kod demonstruje podstawowe funkcje tej klasy i przykładowe wyniki. Ze względu na niedeterministyczną naturę `random_device` wartości losowe wyświetlane w sekcji **Output** nie są zgodne z wynikami. Jest to normalne i oczekiwane.

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

Ten przykład jest uproszczony i nie jest reprezentatywny dla ogólnego przypadku użycia dla tego generatora. Aby uzyskać bardziej reprezentatywny przykład kodu, zobacz [\<random>](../standard-library/random.md) .

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<random>

**Przestrzeń nazw:** std

## <a name="random_devicerandom_device"></a><a name="random_device"></a> random_device:: random_device

Konstruuje Generator.

```cpp
random_device(const std::string& = "");
```

### <a name="remarks"></a>Uwagi

Konstruktor inicjuje generator w razie konieczności, ignorując parametr ciągu. Zwraca wartość typu zdefiniowanego przez implementację wychodzącą z [wyjątku](../standard-library/exception-class.md) , jeśli nie można `random_device` zainicjować.

## <a name="random_deviceentropy"></a><a name="entropy"></a> random_device:: Entropia

Szacuje losowość źródła.

```cpp
double entropy() const noexcept;
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca oszacowanie losowości źródła, mierzoną w bitach.

## <a name="random_deviceoperator"></a><a name="op_call"></a> random_device:: operator ()

Zwraca wartość losową.

```cpp
result_type operator()();
```

### <a name="remarks"></a>Uwagi

Zwraca wartości równomiernie dystrybuowane w zamkniętym interwale [ `min, max` ] określone przez funkcje członkowskie `min()` i `max()` . Zwraca wartość typu zdefiniowanego przez implementację wychodzącą z [wyjątku](../standard-library/exception-class.md) , jeśli nie można uzyskać liczby losowej.

## <a name="see-also"></a>Zobacz też

[\<random>](../standard-library/random.md)
