---
title: Rozpoznawanie nazwy dla typów zależnych
ms.date: 11/04/2016
ms.assetid: 34066bb4-0c79-4fd8-bda7-539a60a277ab
ms.openlocfilehash: de40bd056fe351e679ff32d9908c068ea4c6752a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227312"
---
# <a name="name-resolution-for-dependent-types"></a>Rozpoznawanie nazwy dla typów zależnych

Użyj **`typename`** dla kwalifikowanych nazw w definicjach szablonów, aby poinformować kompilator, że dana kwalifikowana nazwa identyfikuje typ. Aby uzyskać więcej informacji, zobacz [TypeName](../cpp/typename.md).

```cpp
// template_name_resolution1.cpp
#include <stdio.h>
template <class T> class X
{
public:
   void f(typename T::myType* mt) {}
};

class Yarg
{
public:
   struct myType { };
};

int main()
{
   X<Yarg> x;
   x.f(new Yarg::myType());
   printf("Name resolved by using typename keyword.");
}
```

```Output
Name resolved by using typename keyword.
```

Funkcja wyszukiwania nazw dla nazw zależnych bada nazwy zarówno z kontekstu definicji szablonu, jak i w poniższym przykładzie ten kontekst będzie znajdował się `myFunction(char)` i kontekst tworzenia wystąpienia szablonu. W poniższym przykładzie szablon został skonkretyzowany jako główny; w związku z tym, `MyNamespace::myFunction` jest widoczna z punktu tworzenia wystąpienia i jest wybierana jako lepsza zgodność. Jeśli `MyNamespace::myFunction` zmieniono nazwę, `myFunction(char)` zostanie ona wywołana.

Wszystkie nazwy są rozpoznawane tak, jakby były nazwami zależnymi. Niemniej jednak zalecamy użycie w pełni kwalifikowanych nazw, jeśli występuje konflikt.

```cpp
// template_name_resolution2.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

void myFunction(char)
{
   cout << "Char myFunction" << endl;
}

template <class T> class Class1
{
public:
   Class1(T i)
   {
      // If replaced with myFunction(1), myFunction(char)
      // will be called
      myFunction(i);
}
};

namespace MyNamespace
{
   void myFunction(int)
   {
      cout << "Int MyNamespace::myFunction" << endl;
   }
};

using namespace MyNamespace;

int main()
{
   Class1<int>* c1 = new Class1<int>(100);
}
```

### <a name="output"></a>Dane wyjściowe

```Output
Int MyNamespace::myFunction
```

### <a name="template-disambiguation"></a>Uściślanie szablonu

Program Visual Studio 2012 wymusza stosowanie standardowych reguł języka C++ 98/03/11 przy użyciu słowa kluczowego "template". W poniższym przykładzie program Visual Studio 2010 akceptuje zarówno niezgodne wiersze, jak i wiersze.  Program Visual Studio 2012 akceptuje tylko wiersze zgodne.

```cpp
#include <iostream>
#include <ostream>
#include <typeinfo>
using namespace std;

template <typename T> struct Allocator {
    template <typename U> struct Rebind {
        typedef Allocator<U> Other;
    };
};

template <typename X, typename AY> struct Container {
    #if defined(NONCONFORMANT)
        typedef typename AY::Rebind<X>::Other AX; // nonconformant
    #elif defined(CONFORMANT)
        typedef typename AY::template Rebind<X>::Other AX; // conformant
    #else
        #error Define NONCONFORMANT or CONFORMANT.
    #endif
};

int main() {
    cout << typeid(Container<int, Allocator<float>>::AX).name() << endl;
}
```

Zgodność z regułami uściślania jest wymagana, ponieważ domyślnie język C++ zakłada, że `AY::Rebind` nie jest to szablon i dlatego kompilator interpretuje następujący element " `<` " jako mniej niż. Musi wiedzieć, że `Rebind` jest to szablon, tak aby mógł prawidłowo analizować " `<` " jako nawias ostry.

## <a name="see-also"></a>Zobacz także

[Rozpoznawanie nazw](../cpp/templates-and-name-resolution.md)
