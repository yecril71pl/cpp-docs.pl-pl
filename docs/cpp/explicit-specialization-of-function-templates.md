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
ms.openlocfilehash: e35eda35a7d2474826ce151292121be224955420
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="explicit-specialization-of-function-templates"></a>Jawna specjalizacja szablonów funkcji
Z szablonem funkcji można zdefiniować specjalnego zachowania w przypadku określonego typu, zapewniając jawna specjalizacja szablonu funkcji (Zastąp) dla tego typu. Na przykład:  
  
```cpp
template<> void MySwap(double a, double b);  
```  
  
 Ta deklaracja umożliwia zdefiniowanie innej funkcji dla **podwójne** zmiennych. Funkcje nieszablonowe, konwersje standardowe, takich jak (np. podwyższenie poziomu zmiennej typu **float** do **podwójne**) są stosowane.  
  
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
