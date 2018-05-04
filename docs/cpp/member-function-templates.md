---
title: Szablony funkcji Członkowskich | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- function templates, member functions
ms.assetid: 83d51835-6a27-40ed-997c-7d90dc9182d8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cb7eeed732f8d9e69dd2571b69cf1c7247a38991
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="member-function-templates"></a>Szablony funkcji członkowskich

Szablon elementu członkowskiego termin odnosi się zarówno szablony funkcji Członkowskich i zagnieżdżone szablony klas. Szablony funkcji Członkowskich są funkcje szablonów, które są członkami klasy lub szablonu klasy.  
  
 Funkcje Członkowskie mogą być szablonów funkcji w kilku sytuacjach. Wszystkie funkcje szablonów klas są ogólne, ale nie są określane jako szablonów elementów członkowskich lub szablony funkcji Członkowskich. Jeśli te funkcje Członkowskie korzystać z własnych argumentów szablonu, są one traktowane jako szablony funkcji Członkowskich.  
  
## <a name="example"></a>Przykład

 Szablony funkcji Członkowskich klas nieszablonu lub w szablonie są deklarowane jako szablonów funkcji z ich parametrów szablonu.  
  
```cpp
// member_function_templates.cpp  
struct X  
{  
   template <class T> void mf(T* t) {}  
};  
  
int main()  
{  
   int i;  
   X* x = new X();  
   x->mf(&i);  
}  
```  
  
## <a name="example"></a>Przykład

 W poniższym przykładzie pokazano element członkowski szablonu funkcji klasy szablonu.  
  
```cpp
// member_function_templates2.cpp  
template<typename T>  
class X  
{  
public:  
   template<typename U>  
   void mf(const U &u)  
   {  
   }  
};  
  
int main()  
{  
}  
```  
  
## <a name="example"></a>Przykład
  
```cpp
// defining_member_templates_outside_class.cpp  
template<typename T>  
class X  
{  
public:  
   template<typename U>  
   void mf(const U &u);  
};  
  
template<typename T> template <typename U>  
void X<T>::mf(const U &u)  
{  
}  
  
int main()  
{  
}  
```  
  
## <a name="example"></a>Przykład

 Klas lokalnych nie mogą posiadać szablonów elementu członkowskiego.  
  
 Funkcje szablonów elementu członkowskiego nie może być funkcji wirtualnych i nie może zastąpić funkcji wirtualnych z klasy podstawowej, gdy są one zgłoszone z taką samą nazwę jak funkcji wirtualnej klasy podstawowej.  
  
W poniższym przykładzie przedstawiono opartego na szablonie konwersji zdefiniowanej przez użytkownika:  
  
```cpp
// templated_user_defined_conversions.cpp  
template <class T>  
struct S  
{  
   template <class U> operator S<U>()  
   {  
      return S<U>();  
   }  
};  
  
int main()  
{  
   S<int> s1;  
   S<long> s2 = s1;  // Convert s1 using UDC and copy constructs S<long>.  
}  
```  
  
## <a name="see-also"></a>Zobacz też

 [Szablony funkcji](../cpp/function-templates.md)
