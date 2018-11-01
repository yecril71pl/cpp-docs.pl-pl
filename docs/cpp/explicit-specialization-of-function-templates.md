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
ms.openlocfilehash: 3d91383f895f1a8be983efe42f685419ca988823
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50665182"
---
# <a name="explicit-specialization-of-function-templates"></a>Jawna specjalizacja szablonów funkcji

Za pomocą funkcji szablonu można zdefiniować specjalne zachowanie dla określonego typu, zapewniając jawna specjalizacja szablonu funkcji (override) dla tego typu. Na przykład:

```cpp
template<> void MySwap(double a, double b);
```

Ta deklaracja umożliwia zdefiniowanie różnych funkcji dla **double** zmiennych. Funkcje nieszablonowe, konwersje standardowe, takie jak (np. promowanie zmienną typu **float** do **double**) są stosowane.

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

## <a name="see-also"></a>Zobacz także

[Szablony funkcji](../cpp/function-templates.md)