---
title: "Typy ogólne i szablony (Visual C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- generics [C++], vs. templates
- templates, C++
ms.assetid: 63adec79-b1dc-4a1a-a21d-b8a72a8fce31
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 307cc39e64a6fd91f3f5f96da634e47d3e9a9030
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="generics-and-templates-visual-c"></a>Typy ogólne i szablony (Visual C++)
Typy ogólne i szablony są obie funkcje języka, które obsługują typy z parametrami. Jednak różnią się od siebie i mają różnych zastosowań. Ten temat zawiera omówienie wiele różnic.  
  
 Aby uzyskać więcej informacji, zobacz [środowiska wykonawczego systemu Windows i zarządzane szablony](../windows/windows-runtime-and-managed-templates-cpp-component-extensions.md).  
  
## <a name="comparing-templates-and-generics"></a>Porównanie szablony i typy ogólne  
 Podstawowe różnice między typy ogólne i szablonów języka C++:  
  
-   Typy ogólne są ogólne, dopóki typy są zastępowane dla nich w czasie wykonywania. Szablony są przystosowane w szczególności w czasie kompilacji, nie są one nadal sparametryzowane typów w czasie wykonywania  
  
-   Środowisko uruchomieniowe języka wspólnego obsługuje określone typy ogólne w MSIL. Ponieważ środowisko uruchomieniowe zna ogólne, określonych typów można zastąpić dla typów ogólnych podczas odwoływania się do zestawu zawierającego typ ogólny. Szablony, natomiast rozwiązania do zwykłych typów w czasie kompilacji, a wynikowy typów nie może być specjalizowany w innych zestawów.  
  
-   Typy ogólne specjalizowany w dwóch różnych zestawów tego samego typu argumenty są tego samego typu. Szablony specjalizowany w dwóch różnych zestawów tego samego typu, który argumenty są uważane przez środowisko uruchomieniowe różnych typów.  
  
-   Typy ogólne są generowane jako pojedynczy kodu wykonywalnego, który służy do wszystkich argumentów typu odwołanie (nie jest to wartość true dla typów wartości, które mają unikatowe implementacji na typ wartości). Kompilator JIT zna ogólne — informacje i jest w stanie Optymalizuj kod dla typów odwołanie lub wartość, które są używane jako argumentów typu. Szablony generować kod oddzielne środowiska uruchomieniowego dla każdej specjalizacji.  
  
-   Typy ogólne nie zezwalaj na parametry szablonu bez typu, takich jak `template <int i> C {}`. Szablony umożliwiają je.  
  
-   Typy ogólne nie zezwalają na jawna specjalizacja (to znaczy implementacja niestandardowa szablonu dla określonego typu). Czy szablony.  
  
-   Typy ogólne nie zezwalają na częściowej specjalizacji (niestandardowej implementacji dla podzbioru argumentów typu). Czy szablony.  
  
-   Typy ogólne nie zezwalają na parametr typu do użycia jako klasę podstawową dla typu ogólnego. Czy szablony.  
  
-   Szablony obsługują parametrów szablonu szablonu (np. `template<template<class T> class X> class MyClass`), ale typy ogólne nie.  
  
## <a name="combining-templates-and-generics"></a>Łączenie szablony i typy ogólne  
  
-   Podstawowa różnica w typach ogólnych ma wpływ na tworzenie aplikacji łączące szablony i typami ogólnymi. Na przykład załóżmy, że masz klasy szablonu, który chcesz utworzyć ogólnego otoki dla do udostępnienia tego szablonu do innych języków jako ogólnego. Podejmij ogólny nie może mieć parametr typu, który następnie przekazuje do szablonu, ponieważ szablon musi mieć typ parametru w czasie kompilacji, ale ogólnych nie rozpoznać parametru typu do środowiska wykonawczego. Zagnieżdżania wewnątrz ogólnego szablonu nie będzie działać albo ponieważ nie ma możliwości rozwiń węzeł Szablony w czasie kompilacji dla dowolnych typów ogólnych, które mogła zostać utworzona w czasie wykonywania.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poniższy przykład przedstawia prosty przykład za pomocą szablonów i typami ogólnymi razem. W tym przykładzie klasa szablonu przekazuje jego parametrów za pomocą typu ogólnego. Sytuacja odwrotna nie jest możliwe.  
  
 Tego idiom można użyć, gdy chcesz skompilować na istniejące ogólnego interfejsu API z kodem szablonu, który jest lokalny dla zestawu Visual C++ lub gdy konieczne jest dodanie dodatkowej warstwy parametryzacja do typu ogólnego, aby móc korzystać z niektórych funkcji szablony nie supporte d przez ogólne.  
  
### <a name="code"></a>Kod  
  
```  
// templates_and_generics.cpp  
// compile with: /clr  
using namespace System;  
  
generic <class ItemType>  
ref class MyGeneric {  
   ItemType m_item;  
  
public:  
   MyGeneric(ItemType item) : m_item(item) {}  
   void F() {   
      Console::WriteLine("F");   
   }  
};  
  
template <class T>  
public ref class MyRef {  
MyGeneric<T>^ ig;  
  
public:  
   MyRef(T t) {  
      ig = gcnew MyGeneric<T>(t);  
      ig->F();  
    }      
};  
  
int main() {  
   // instantiate the template  
   MyRef<int>^ mref = gcnew MyRef<int>(11);  
}  
```  
  
### <a name="output"></a>Dane wyjściowe  
  
```  
F  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Typy ogólne](../windows/generics-cpp-component-extensions.md)