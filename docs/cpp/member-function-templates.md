---
title: Szablony funkcji członkowskich
ms.date: 11/04/2016
helpviewer_keywords:
- function templates, member functions
ms.assetid: 83d51835-6a27-40ed-997c-7d90dc9182d8
ms.openlocfilehash: ee36d4f33f3e4216e2ad9c434ac1da4ca3aa83e8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177984"
---
# <a name="member-function-templates"></a>Szablony funkcji członkowskich

Termin szablon elementu członkowskiego odwołuje się zarówno do szablonów funkcji składowych, jak i szablonów klas zagnieżdżonych. Szablony funkcji Członkowskich są funkcjami szablonu, które są elementami członkowskimi szablonu klasy lub klasy.

Funkcje składowe mogą być szablonami funkcji w kilku kontekstach. Wszystkie funkcje szablonów klas są ogólne, ale nie są określane jako szablony elementów członkowskich lub szablony funkcji składowych. Jeśli te funkcje elementu członkowskiego korzystają z własnych argumentów szablonu, są one uznawane za szablony funkcji składowych.

## <a name="example"></a>Przykład

Szablony funkcji członkowskich klas nienależących do szablonu lub szablonu są deklarowane jako szablony funkcji ze swoimi parametrami szablonu.

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

Poniższy przykład pokazuje szablon funkcji składowej klasy szablonu.

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

Lokalne klasy nie mogą mieć szablonów składowych.

Funkcje szablonu elementu członkowskiego nie mogą być funkcjami wirtualnymi i nie mogą przesłonić funkcji wirtualnych z klasy podstawowej, gdy są one zadeklarowane przy użyciu takiej samej nazwy jak funkcja wirtualna klasy bazowej.

W poniższym przykładzie przedstawiono zdefiniowaną przez użytkownika konwersję:

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
