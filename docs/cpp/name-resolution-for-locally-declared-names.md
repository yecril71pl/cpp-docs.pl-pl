---
title: Rozpoznawanie nazw dla lokalnie zadeklarowanych nazw | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 743b88f3-de11-48f4-ae83-931449ea3886
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3a250a6a357cf0c8a8b3d01e241b6286f69b842b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46021002"
---
# <a name="name-resolution-for-locally-declared-names"></a>Rozpoznawanie nazwy dla lokalnie zadeklarowanych nazw

Sama nazwa szablonu może być określona z argumentami szablonu lub też bez nich. W zakresie szablonu klasy sama nazwa odnosi się do szablonu. W zakresie specjalizacji lub częściowej specjalizacji szablonu sama nazwa odnosi się do specjalizacji lub częściowej specjalizacji. Można się również odwoływać do innych specjalizacji lub częściowych specjalizacji szablonu, z argumentami odpowiedniego szablonu.

## <a name="example"></a>Przykład

Poniższy kod pokazuje, że nazwa szablonu klasy A jest interpretowana inaczej w zakresie specjalizacji lub częściowej specjalizacji.

```cpp
// template_name_resolution3.cpp
// compile with: /c
template <class T> class A {
   A* a1;   // A refers to A<T>
   A<int>* a2;  // A<int> refers to a specialization of A.
   A<T*>* a3;   // A<T*> refers to the partial specialization A<T*>.
};

template <class T> class A<T*> {
   A* a4; // A refers to A<T*>.
};

template<> class A<int> {
   A* a5; // A refers to A<int>.
};
```

## <a name="example"></a>Przykład

W przypadku konfliktu nazw między parametrem szablonu i innym obiektem, parametr szablonu może lub nie może być ukryty. Następujące reguły pomogą określić pierwszeństwo.

Parametr szablonu jest w zakresie od punktu, gdzie po raz pierwszy występuje aż do końca szablonu klasy lub funkcji. Jeśli nazwa pojawi się ponownie na liście argumentów szablonu lub na liście klas bazowych, dotyczy ona tego samego typu. W standardzie języka C++ żadna inna nazwa, która jest identyczna z parametrem szablonu nie może być zadeklarowana w tym samym zakresie. Rozszerzenie Microsoft pozwala przedefiniować parametr szablonu na nowo w zakresie szablonu. Poniższy przykład pokazuje użycie parametru szablonu w podstawowej specyfikacji szablonu klasy.

```cpp
// template_name_resolution4.cpp
// compile with: /EHsc
template <class T>
class Base1 {};

template <class T>
class Derived1 : Base1<T> {};

int main() {
   // Derived1<int> d;
}
```

## <a name="example"></a>Przykład

Podczas definiowania funkcji skkładowych szablonu poza szablonem klasy nazwy parametru może używać inny szablon. Jeśli definicja funkcji członkowskiej szablonu używa innej nazwy parametru szablonu, niż ta zgłoszona, a nazwa używana w definicji powoduje konflikt z innym elementem członkowskim deklaracji, element członkowski w deklaracji szablonu ma pierwszeństwo.

```cpp
// template_name_resolution5.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

template <class T> class C {
public:
   struct Z {
      Z() { cout << "Z::Z()" << endl; }
   };
   void f();
};

template <class Z>
void C<Z>::f() {
   // Z refers to the struct Z, not to the template arg;
   // Therefore, the constructor for struct Z will be called.
   Z z;
}

int main() {
   C<int> c;
   c.f();
}
```

```Output
Z::Z()
```

## <a name="example"></a>Przykład

Podczas definiowania funkcji szablonu lub funkcji członkowskiej poza przestrzenią nazw, w której został zadeklarowany szablon, argument szablonu ma pierwszeństwo przed nazwami innych elementów członkowskich przestrzeni nazw.

```cpp
// template_name_resolution6.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

namespace NS {
   void g() { cout << "NS::g" << endl; }

   template <class T> struct C {
      void f();
      void g() { cout << "C<T>::g" << endl; }
   };
};

template <class T>
void NS::C<T>::f() {
   g(); // C<T>::g, not NS::g
};

int main() {
   NS::C<int> c;
   c.f();
}
```

```Output
C<T>::g
```

## <a name="example"></a>Przykład

W definicjach, które nie należą do deklaracji klasy szablonu, jeśli klasa szablonu ma klasę podstawową, która nie zależy od argumentu szablonu i jeśli klasa podstawowa lub jedna z jej składowych ma taką samą nazwę jak argument szablonu, wówczas klasa podstawowa lub nazwa składowej ukrywa argument szablonu.

```cpp
// template_name_resolution7.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

struct B {
   int i;
   void print() { cout << "Base" << endl; }
};

template <class T, int i> struct C : public B {
   void f();
};

template <class B, int i>
void C<B, i>::f() {
   B b;   // Base class b, not template argument.
   b.print();
   i = 1; // Set base class's i to 1.
}

int main() {
   C<int, 1> c;
   c.f();
   cout << c.i << endl;
}
```

```Output
Base
1
```

## <a name="see-also"></a>Zobacz także

[Rozpoznawanie nazw](../cpp/templates-and-name-resolution.md)