---
title: 'Operator rozpoznawania zakresów: ::'
ms.date: 11/04/2016
f1_keywords:
- '::'
helpviewer_keywords:
- scope, scope resolution operator
- operators [C++], scope resolution
- scope resolution operator
- ':: operator'
ms.assetid: fd5de9d3-c716-4e12-bae9-03a16fd79a50
ms.openlocfilehash: 07c2884ed0ba114c22a0c71bbaf7268d6f6931a4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178889"
---
# <a name="scope-resolution-operator-"></a>Operator rozpoznawania zakresów: ::

Operator rozpoznawania zakresu **::** służy do identyfikowania i niejednoznaczności identyfikatorów używanych w różnych zakresach. Aby uzyskać więcej informacji na temat zakresu, zobacz [SCOPE](../cpp/scope-visual-cpp.md).

## <a name="syntax"></a>Składnia

```
:: identifier
class-name :: identifier
namespace :: identifier
enum class :: identifier
enum struct :: identifier
```

## <a name="remarks"></a>Uwagi

`identifier` może być zmienną, funkcją lub wartością wyliczenia.

## <a name="with-classes-and-namespaces"></a>Z klasami i przestrzeniami nazw

Poniższy przykład pokazuje, jak operator rozpoznawania zakresu jest używany z przestrzeniami nazw i klasami:

```cpp
namespace NamespaceA{
    int x;
    class ClassA {
    public:
        int x;
    };
}

int main() {

    // A namespace name used to disambiguate
    NamespaceA::x = 1;

    // A class name used to disambiguate
    NamespaceA::ClassA a1;
    a1.x = 2;
}
```

Operator rozpoznawania zakresu bez kwalifikatora zakresu odwołuje się do globalnej przestrzeni nazw.

```cpp
namespace NamespaceA{
    int x;
}

int x;

int main() {
    int x;

    // the x in main()
    x = 0;
    // The x in the global namespace
    ::x = 1;

    // The x in the A namespace
    NamespaceA::x = 2;
}
```

Możesz użyć operatora rozpoznawania zakresu, aby zidentyfikować element członkowski przestrzeni nazw lub zidentyfikować przestrzeń nazw, która wyznacza przestrzeń nazw składowej w dyrektywie using. W poniższym przykładzie można użyć `NamespaceC`, aby zakwalifikować `ClassB`, nawet jeśli `ClassB` został zadeklarowany w `NamespaceB`przestrzeni nazw, ponieważ `NamespaceB` został wyznaczony w `NamespaceC` przez dyrektywę using.

```cpp
namespace NamespaceB {
    class ClassB {
    public:
        int x;
    };
}

namespace NamespaceC{
    using namespace B;
}
int main() {
    NamespaceB::ClassB c_b;
    NamespaceC::ClassB c_c;

    c_b.x = 3;
    c_c.x = 4;
}
```

Można używać łańcuchów operatorów rozpoznawania zakresu. W poniższym przykładzie `NamespaceD::NamespaceD1` identyfikuje zagnieżdżoną przestrzeń nazw `NamespaceD1`, a `NamespaceE::ClassE::ClassE1` określa klasę zagnieżdżoną `ClassE1`.

```cpp
namespace NamespaceD{
    namespace NamespaceD1{
        int x;
    }
}

namespace NamespaceE{
    class ClassE{
    public:
        class ClassE1{
        public:
            int x;
        };
    };
}

int main() {
    NamespaceD:: NamespaceD1::x = 6;
    NamespaceE::ClassE::ClassE1 e1;
    e1.x = 7  ;
}
```

## <a name="with-static-members"></a>Ze statycznymi składowymi

Aby wywołać statyczne elementy członkowskie klas, należy użyć operatora rozpoznawania zakresu.

```cpp
class ClassG {
public:
    static int get_x() { return x;}
    static int x;
};

int ClassG::x = 6;

int main() {

    int gx1 = ClassG::x;
    int gx2 = ClassG::get_x();
}
```

## <a name="with-scoped-enumerations"></a>Z wyliczeniem w zakresie

Operator rozpoznania zakresu jest również używany z wartościami [deklaracji wyliczenia](../cpp/enumerations-cpp.md)wyliczeniowego w zakresie, jak w poniższym przykładzie:

```cpp
enum class EnumA{
    First,
    Second,
    Third
};

int main() {
    EnumA enum_value = EnumA::First;
}
```

## <a name="see-also"></a>Zobacz też

[Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Przestrzenie nazw](../cpp/namespaces-cpp.md)
