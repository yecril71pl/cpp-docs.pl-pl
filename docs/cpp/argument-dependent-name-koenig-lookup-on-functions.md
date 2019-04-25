---
title: Odnośnik do nazwy zależnej od argumentu (Koenig) funkcji
ms.date: 11/04/2016
helpviewer_keywords:
- Koenig lookup
- argument-dependent lookup [C++]
ms.assetid: c0928401-da2c-4658-942d-9ba4df149c35
ms.openlocfilehash: d979b79c0f712ed35a42a44047dd1091010c72bf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62184482"
---
# <a name="argument-dependent-name-koenig-lookup-on-functions"></a>Odnośnik do nazwy zależnej od argumentu (Koenig) funkcji

Kompilator może być Znajdź definicję wywołanie funkcji niekwalifikowanej odnośnik do nazwy zależnej od argumentu. Odnośnik do nazwy zależnej od argumentu jest również nazywany wyszukiwanie Koeniga. Typ każdego argumentu w wywołaniu funkcji jest zdefiniowany w ramach hierarchii przestrzenie nazw, klasy, struktury, Unii lub szablonów. Po określeniu niekwalifikowanej [przyrostkowe](../cpp/postfix-expressions.md) wywołanie funkcji, kompilator szuka definicji funkcji w hierarchii, skojarzone z poszczególnymi typami argumentów.

## <a name="example"></a>Przykład

W tym przykładzie kompilator — informacje o tej funkcji `f()` przyjmuje argument `x`. Argument `x` typu `A::X`, który jest zdefiniowany w przestrzeni nazw `A`. Kompilator wyszukuje przestrzeni nazw `A` i odnajduje definicję funkcji `f()` która przyjmuje argument typu `A::X`.

```cpp
// argument_dependent_name_koenig_lookup_on_functions.cpp
namespace A
{
   struct X
   {
   };
   void f(const X&)
   {
   }
}
int main()
{
// The compiler finds A::f() in namespace A, which is where
// the type of argument x is defined. The type of x is A::X.
   A::X x;
   f(x);
}
```