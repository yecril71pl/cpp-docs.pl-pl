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
ms.openlocfilehash: 611fe53b960a7c8f80990240aa4fc8ac4affb606
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87187403"
---
# <a name="__if_exists-statement"></a>__if_exists — Instrukcja

**`__if_exists`** Instrukcja testuje, czy określony identyfikator istnieje. Jeśli identyfikator istnieje, zostanie wykonany określony blok instrukcji.

## <a name="syntax"></a>Składnia

```
__if_exists ( identifier ) {
statements
};
```

#### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*identyfikatora*|Identyfikator, którego istnienie ma zostać przetestowane.|
|*zatwierdzeni*|Jedna lub więcej instrukcji do wykonania, jeśli *Identyfikator* istnieje.|

## <a name="remarks"></a>Uwagi

> [!CAUTION]
> Aby uzyskać najbardziej niezawodne wyniki, użyj **`__if_exists`** instrukcji w ramach następujących ograniczeń.

- Zastosuj **`__if_exists`** instrukcję tylko do typów prostych, a nie szablonów.

- Zastosuj **`__if_exists`** instrukcję do identyfikatorów zarówno wewnątrz, jak i poza klasą. Nie stosuj **`__if_exists`** instrukcji do zmiennych lokalnych.

- Użyj **`__if_exists`** instrukcji tylko w treści funkcji. Poza treścią funkcji, **`__if_exists`** instrukcja może testować tylko w pełni zdefiniowane typy.

- Podczas testowania dla przeciążonych funkcji nie można testować pod kątem określonej formy przeciążenia.

Uzupełnienie **`__if_exists`** instrukcji jest instrukcją [__if_not_exists](../cpp/if-not-exists-statement.md) .

## <a name="example"></a>Przykład

Zwróć uwagę, że w tym przykładzie są używane szablony, które nie są zalecane.

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

## <a name="see-also"></a>Zobacz także

[Instrukcje wyboru](../cpp/selection-statements-cpp.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[Instrukcja __if_not_exists](../cpp/if-not-exists-statement.md)
