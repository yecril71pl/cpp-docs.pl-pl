---
title: Jawna specjalizacja szablonów funkcji
ms.date: 11/04/2016
helpviewer_keywords:
- overriding, functions
- function templates, specialization
- explicit specialization of function templates
- declaring functions [C++], specialization of function template
- specialization of function templates
ms.assetid: eb0fcb73-eaed-42a1-9b83-14b055a34bf8
ms.openlocfilehash: c9d77cef790bdd0a65651ffb7246e685175482b1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179994"
---
# <a name="explicit-specialization-of-function-templates"></a>Jawna specjalizacja szablonów funkcji

Za pomocą szablonu funkcji można zdefiniować specjalne zachowanie dla określonego typu, podając jawną specjalizację (przesłonięcie) szablonu funkcji dla tego typu. Na przykład:

```cpp
template<> void MySwap(double a, double b);
```

Ta deklaracja umożliwia zdefiniowanie innej funkcji dla zmiennych **podwójnie** . Podobnie jak w przypadku funkcji innych niż szablony, stosowane są standardowe konwersje typów (takie jak podwyższanie poziomu zmiennej typu **float** do **Double**).

## <a name="example"></a>Przykład

```cpp
// explicit_specialization.cpp
template<class T> void f(T t)
{
};

// Explicit specialization of f with 'char' with the
// template argument explicitly specified:
//
template<> void f<char>(char c)
{
}

// Explicit specialization of f with 'double' with the
// template argument deduced:
//
template<> void f(double d)
{
}
int main()
{
}
```

## <a name="see-also"></a>Zobacz też

[Szablony funkcji](../cpp/function-templates.md)
