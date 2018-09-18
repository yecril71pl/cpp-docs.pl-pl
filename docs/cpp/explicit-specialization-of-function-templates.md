---
title: Jawna specjalizacja szablonów funkcji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- overriding, functions
- function templates, specialization
- explicit specialization of function templates
- declaring functions [C++], specialization of function template
- specialization of function templates
ms.assetid: eb0fcb73-eaed-42a1-9b83-14b055a34bf8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3070108e9e85273a86b93d40301747b658ae231b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46029029"
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