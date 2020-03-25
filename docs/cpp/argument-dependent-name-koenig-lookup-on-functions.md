---
title: Odnośnik do nazwy zależnej od argumentu (Koenig) funkcji
ms.date: 11/04/2016
helpviewer_keywords:
- Koenig lookup
- argument-dependent lookup [C++]
ms.assetid: c0928401-da2c-4658-942d-9ba4df149c35
ms.openlocfilehash: 88811e8070fdfe398bc12734221dee772515d8bc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190540"
---
# <a name="argument-dependent-name-koenig-lookup-on-functions"></a>Odnośnik do nazwy zależnej od argumentu (Koenig) funkcji

Kompilator może użyć wyszukiwania nazw zależnych od argumentów, aby znaleźć definicję niekwalifikowanego wywołania funkcji. Funkcja wyszukiwania nazw zależnych od argumentów jest również nazywana Koenig Lookup. Typ każdego argumentu w wywołaniu funkcji jest zdefiniowany w hierarchii przestrzeni nazw, klas, struktur, Unii lub szablonów. W przypadku określenia niekwalifikowanego wywołania funkcji [przyrostkowej](../cpp/postfix-expressions.md) Kompilator wyszukuje definicję funkcji w hierarchii skojarzonej z każdym typem argumentu.

## <a name="example"></a>Przykład

W przykładzie, kompilator uwagi, że funkcja `f()` przyjmuje argument `x`. Argument `x` jest typu `A::X`, który jest zdefiniowany w `A`przestrzeni nazw. Kompilator przeszukuje przestrzeń nazw `A` i znajduje definicję funkcji `f()`, która przyjmuje argument typu `A::X`.

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
