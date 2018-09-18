---
title: Wyszukiwanie nazwy zależnej od argumentu (Koenig) funkcji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- Koenig lookup
- argument-dependent lookup [C++]
ms.assetid: c0928401-da2c-4658-942d-9ba4df149c35
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8e71a1fd5a795fb95520ec8d7859e70460a9372c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46028821"
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