---
title: __if_exists — Instrukcja
ms.date: 11/04/2016
f1_keywords:
- __if_exists_cpp
helpviewer_keywords:
- identifiers, testing for existence
- symbols, testing for existence
- __if_exists keyword [C++]
ms.assetid: d3eb34b6-f3a9-4063-a286-b62a28c0c7fa
ms.openlocfilehash: 609d576c6ab3eddca569ed4f19a4024b47b6a1d2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374149"
---
# <a name="__if_exists-statement"></a>__if_exists — Instrukcja

Instrukcja **__if_exists** sprawdza, czy określony identyfikator istnieje. Jeśli identyfikator istnieje, wykonywany jest określony blok instrukcji.

## <a name="syntax"></a>Składnia

```
__if_exists ( identifier ) {
statements
};
```

#### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Identyfikator*|Identyfikator, którego istnienie chcesz przetestować.|
|*Instrukcji*|Co najmniej jedna instrukcja do wykonania, jeśli istnieje *identyfikator.*|

## <a name="remarks"></a>Uwagi

> [!CAUTION]
> Aby uzyskać najbardziej wiarygodne wyniki, należy użyć **instrukcji __if_exists** w następujących ograniczeniach.

- Zastosuj **instrukcję __if_exists** tylko do typów prostych, a nie szablonów.

- Zastosuj **__if_exists** instrukcji do identyfikatorów zarówno wewnątrz, jak i na zewnątrz klasy. Nie należy stosować **instrukcji __if_exists** do zmiennych lokalnych.

- Instrukcja **__if_exists** należy używać tylko w treści funkcji. Poza treścią **funkcji, __if_exists** instrukcja może testować tylko w pełni zdefiniowane typy.

- Podczas testowania funkcji przeciążonych, nie można przetestować dla określonej formy przeciążenia.

Uzupełnieniem **oświadczenia __if_exists** jest oświadczenie [__if_not_exists.](../cpp/if-not-exists-statement.md)

## <a name="example"></a>Przykład

Należy zauważyć, że w tym przykładzie używa szablonów, co nie jest zalecane.

```cpp
// the__if_exists_statement.cpp
// compile with: /EHsc
#include <iostream>

template<typename T>
class X : public T {
public:
   void Dump() {
      std::cout << "In X<T>::Dump()" << std::endl;

      __if_exists(T::Dump) {
         T::Dump();
      }

      __if_not_exists(T::Dump) {
         std::cout << "T::Dump does not exist" << std::endl;
      }
   }
};

class A {
public:
   void Dump() {
      std::cout << "In A::Dump()" << std::endl;
   }
};

class B {};

bool g_bFlag = true;

class C {
public:
   void f(int);
   void f(double);
};

int main() {
   X<A> x1;
   X<B> x2;

   x1.Dump();
   x2.Dump();

   __if_exists(::g_bFlag) {
      std::cout << "g_bFlag = " << g_bFlag << std::endl;
   }

   __if_exists(C::f) {
      std::cout << "C::f exists" << std::endl;
   }

   return 0;
}
```

## <a name="output"></a>Dane wyjściowe

```Output
In X<T>::Dump()
In A::Dump()
In X<T>::Dump()
T::Dump does not exist
g_bFlag = 1
C::f exists
```

## <a name="see-also"></a>Zobacz też

[Instrukcje wyboru](../cpp/selection-statements-cpp.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[__if_not_exists, instrukcja](../cpp/if-not-exists-statement.md)
