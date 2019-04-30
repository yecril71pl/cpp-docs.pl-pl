---
title: Szablony funkcji członkowskich
ms.date: 11/04/2016
helpviewer_keywords:
- function templates, member functions
ms.assetid: 83d51835-6a27-40ed-997c-7d90dc9182d8
ms.openlocfilehash: 6955d755897d326479d2b3789edb02ff66806175
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345971"
---
# <a name="member-function-templates"></a>Szablony funkcji członkowskich

Termin szablonem składowej odnosi się do zarówno szablony funkcji składowych i zagnieżdżone szablony klas. Szablony funkcji Członkowskich są funkcje szablonu, które należą do klasy lub szablonu klasy.

Funkcje składowe mogą być szablonów funkcji w wielu kontekstach. Wszystkie funkcje szablonów klas są rodzajowe, ale nie są określone jako szablony składowych lub szablony funkcji Członkowskich. Jeśli te funkcje elementów członkowskich wykonać swoje własne argumentów szablonu, są one traktowane jako szablony funkcji Członkowskich.

## <a name="example"></a>Przykład

Szablony funkcji składowych klas nieszablonu lub szablonu są deklarowane jako szablony funkcji za pomocą swoich parametrów szablonu.

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

W poniższym przykładzie pokazano element członkowski funkcji szablonu klasy szablonu.

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

Klasy lokalnej nie mogą mieć szablonów składowych.

Szablon elementów członkowskich nie może mieć funkcji wirtualnych i nie można przesłonić funkcje wirtualne z klasy bazowej, gdy są one zadeklarowane z taką samą nazwę jak funkcją wirtualną klasę bazową.

Poniższy przykład przedstawia oparte na szablonach konwersja zdefiniowana przez użytkownika:

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

## <a name="see-also"></a>Zobacz także

[Szablony funkcji](../cpp/function-templates.md)