---
title: random_device — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- random/std::random_device
- random/std::random_device::min
- random/std::random_device::max
- random/std::random_device::entropy
- random/std::random_device::operator()
dev_langs:
- C++
helpviewer_keywords:
- std::random_device [C++]
- std::random_device [C++], min
- std::random_device [C++], max
- std::random_device [C++], entropy
- std::random_device [C++], entropy
ms.assetid: 4393d515-0cb6-4e0d-a2ba-c780f05dc1bf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1ac22e146ac305be92d0b4be214465e64e8b6873
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33856114"
---
# <a name="randomdevice-class"></a>random_device — Klasa

Generuje losowe sekwencji z zewnętrznego urządzenia.

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

Klasa opisuje źródła liczb losowych i jest dozwolone, ale nie musi być deterministyczna lub kryptograficznie bezpieczny standard C++ ISO. W programie Visual Studio implementacji wartości tworzone są deterministyczna i zabezpieczone kryptograficznie, ale działa wolniej niż utworzone na podstawie aparaty i adapterów aparat generatory (takich jak [mersenne_twister_engine —](../standard-library/mersenne-twister-engine-class.md), wysokiej jakości i szybki aparat wyboru dla większości aplikacji).

`random_device` wyniki mogą być równomiernie rozłożone w zakresie zamknięte [ `0, 2` <sup>32</sup>).

`random_device` nie jest gwarantowana spowodować nieblokujące wywołania.

Ogólnie rzecz biorąc `random_device` jest używany do generowania innych generatory utworzone za pomocą aparatów lub adapterów aparatu. Aby uzyskać więcej informacji, zobacz [ \<losowe >](../standard-library/random.md).

## <a name="example"></a>Przykład

Poniższy kod przedstawia podstawowe funkcje to klasa i przykładowe wyniki. Z powodu deterministyczna rodzaj `random_device`, losowych wartości widoczne w **dane wyjściowe** sekcji będzie niezgodna z wyników. Jest to normalne i oczekiwana.

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

W tym przykładzie jest simplistic i nie reprezentatywny dla ogólnych przypadek użycia dla tego generatora. Aby bardziej reprezentatywny przykład kodu, zobacz [ \<losowe >](../standard-library/random.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<losowe >

**Namespace:** Standard

## <a name="random_device"></a>  random_device::random_device

Tworzy generator.

```cpp
random_device(const std::string& = "");
```

### <a name="remarks"></a>Uwagi

Konstruktor inicjuje generatora zgodnie z potrzebami, ignorowanie parametr ciągu. Zwraca wartość typu zdefiniowane w implementacji pochodzące z [wyjątek](../standard-library/exception-class.md) Jeśli `random_device` nie można zainicjować obiektu.

## <a name="entropy"></a>  random_device::Entropy

Szacuje losowości źródła.

```cpp
double entropy() const noexcept;
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca szacunkową losowości źródła, mierzony w bitach.

## <a name="op_call"></a>  random_device::operator()

Zwraca wartość losowa.

```cpp
result_type operator()();
```

### <a name="remarks"></a>Uwagi

Zwraca wartości równomiernie w interwale zamknięte [ `min, max`] zgodnie z ustaleniami funkcji Członkowskich `min()` i `max()`. Zwraca wartość typu zdefiniowane w implementacji pochodzące z [wyjątek](../standard-library/exception-class.md) Jeśli nie można uzyskać liczbę losową.

## <a name="see-also"></a>Zobacz także

[\<losowe >](../standard-library/random.md)<br/>
