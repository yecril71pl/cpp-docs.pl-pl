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
ms.openlocfilehash: 184513bc63975bd8eaaf0e53300e5a6be7986389
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448538"
---
# <a name="randomdevice-class"></a>random_device — Klasa

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

Klasa opisuje źródło liczb losowych i jest dozwolona, ale nie musi być deterministyczna lub kryptograficznie zabezpieczona przez standard ISO C++ . W implementacji programu Visual Studio wartości wyprodukowane są niedeterministyczne i kryptograficznie zabezpieczone, ale działają wolniej niż generatory utworzone na podstawie silników i adapterów silnikowych (takich jak [mersenne_twister_engine](../standard-library/mersenne-twister-engine-class.md), wysoka jakość i szybka silnik wyboru dla większości aplikacji).

`random_device`wyniki są równomiernie dystrybuowane w zamkniętym zakresie `0, 2`[ <sup>32</sup>).

`random_device`nie gwarantuje wyniku wywołania nieblokującego.

Ogólnie rzecz `random_device` biorąc, jest używany do wypełniania innych generatorów utworzonych za pomocą aparatów lub adapterów silników. Aby uzyskać więcej informacji, zobacz [ \<> losowe](../standard-library/random.md).

## <a name="example"></a>Przykład

Poniższy kod demonstruje podstawowe funkcje tej klasy i przykładowe wyniki. Ze względu na niedeterministyczną naturę `random_device`wartości losowe wyświetlane w sekcji **Output** nie są zgodne z wynikami. Jest to normalne i oczekiwane.

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

Ten przykład jest uproszczony i nie jest reprezentatywny dla ogólnego przypadku użycia dla tego generatora. Aby uzyskać bardziej reprezentatywny przykład kodu, zobacz [ \<Random >](../standard-library/random.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<losowe >

**Przestrzeń nazw:** std

## <a name="random_device"></a>random_device::random_device

Konstruuje Generator.

```cpp
random_device(const std::string& = "");
```

### <a name="remarks"></a>Uwagi

Konstruktor inicjuje generator w razie konieczności, ignorując parametr ciągu. Zwraca wartość typu zdefiniowanego przez implementację wychodzącą z [wyjątku](../standard-library/exception-class.md) , `random_device` Jeśli nie można zainicjować.

## <a name="entropy"></a>random_device:: Entropia

Szacuje losowość źródła.

```cpp
double entropy() const noexcept;
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca oszacowanie losowości źródła, mierzoną w bitach.

## <a name="op_call"></a>random_device:: operator ()

Zwraca wartość losową.

```cpp
result_type operator()();
```

### <a name="remarks"></a>Uwagi

Zwraca wartości równomiernie dystrybuowane w zamkniętym interwale `min, max`[] określone przez funkcje `min()` Członkowskie i `max()`. Zwraca wartość typu zdefiniowanego przez implementację wychodzącą z [wyjątku](../standard-library/exception-class.md) , jeśli nie można uzyskać liczby losowej.

## <a name="see-also"></a>Zobacz także

[\<random>](../standard-library/random.md)
