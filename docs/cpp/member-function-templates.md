---
title: Szablony funkcji składowych | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 1c0d7a50be0ab940ebff82cd8a21fb5ac3aed075
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46107007"
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