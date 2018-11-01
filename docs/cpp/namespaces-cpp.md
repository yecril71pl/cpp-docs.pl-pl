---
title: Przestrzenie nazw (C++)
ms.date: 08/30/2017
f1_keywords:
- namespace_CPP
- using_CPP
helpviewer_keywords:
- namespaces [C++], C++
- namespaces [C++]
- namespaces [C++], global
- global namespace
- Visual C++, namespaces
ms.assetid: d1a5a9ab-1cad-47e6-a82d-385bb77f4188
ms.openlocfilehash: 532fdcb5de179bd2fdeb25091ace7210d55a2658
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50508853"
---
# <a name="namespaces-c"></a>Przestrzenie nazw (C++)

Przestrzeń nazw jest deklaratywne region, który obejmuje zakres do identyfikatorów (nazwy typów, funkcje, zmienne itp.) wewnątrz niego. Przestrzenie nazw są używane do organizowania kodu w logiczne grupy i aby zapobiec kolizjom nazw, które mogą wystąpić, szczególnie w przypadku, gdy bazy kodu obejmuje wiele bibliotek. Wszystkie identyfikatory w zakresie przestrzeni nazw są widoczne dla siebie nawzajem bez kwalifikacji. Identyfikatory poza przestrzenią nazw, mogą uzyskiwać dostęp do elementów członkowskich przy użyciu w pełni kwalifikowanej nazwy dla każdego identyfikatora, na przykład `std::vector<std::string> vec;`, lub przez [użycie — deklaracja](../cpp/using-declaration.md) dla pojedynczego identyfikatora (`using std::string`), lub [użycie dyrektywy](../cpp/namespaces-cpp.md#using_directives) dla wszystkich identyfikatorów w przestrzeni nazw (`using namespace std;`). Kod w plikach nagłówkowych zawsze należy używać w pełni kwalifikowanej nazwy obszaru nazw.

W poniższym przykładzie pokazano deklarację przestrzeni nazw i trzy sposoby na to, że kod poza przestrzenią nazw, można uzyskuje dostęp do swoich elementów członkowskich.

```cpp
namespace ContosoData
{
    class ObjectManager
    {
    public:
        void DoSomething() {}
    };
    void Func(ObjectManager) {}
}
```

Użyj w pełni kwalifikowana nazwa:

```cpp
ContosoData::ObjectManager mgr;
mgr.DoSomething();
ContosoData::Func(mgr);
```

Użyj, przy użyciu deklaracji w celu umożliwienia jeden identyfikator zakresu:

```cpp
using ContosoData::ObjectManager;
ObjectManager mgr;
mgr.DoSomething();
```

Użyj, przy użyciu dyrektywy, aby wyświetlić wszystkie elementy w przestrzeni nazw do zakresu:

```cpp
using namespace ContosoData;

ObjectManager mgr;
mgr.DoSomething();
Func(mgr);
```

## <a id="using_directives"></a> dyrektywy Using

**Przy użyciu** dyrektywy zezwala na wszystkie nazwy **przestrzeni nazw** bez *nazwę przestrzeni nazw* jako jawne kwalifikator. Użyj, przy użyciu dyrektywy w pliku implementacji (tj. *.cpp), korzystając z kilku różnych identyfikatorów w przestrzeni nazw; Jeśli używane są tylko jeden lub dwa identyfikatory, rozważ użycie deklaracji tylko zapewnić tych identyfikatorów zakresu i nie wszystkie identyfikatory w przestrzeni nazw. Jeśli zmienna lokalna ma taką samą nazwę jak zmienna przestrzeni nazw, zmienna przestrzeni nazw jest ukryty. Jest to błąd, mieć zmienną o takiej samej nazwie jako zmiennej globalnej przestrzeni nazw.

> [!NOTE]
>  Using — dyrektywa można umieścić w górnej części pliku .cpp (w zakresie pliku), lub wewnątrz definicji klasy lub funkcji.
>
>  Ogólnie rzecz biorąc, należy unikać umieszczania w plikach nagłówkowych przy użyciu dyrektyw (* .h) ponieważ każdego pliku, który zawiera ten nagłówek zostanie wyświetlone wszystkie elementy w przestrzeni nazw do zakresu, które mogą powodować ukrywaniem nazwy oraz problemy kolizji nazw, które są bardzo trudno debugować. Zawsze używaj w pełni kwalifikowanych nazw w pliku nagłówkowym. Jeśli te nazwy zbyt długo, można użyć aliasu przestrzeni nazw skrócić je. (Zobacz poniżej).

## <a name="declaring-namespaces-and-namespace-members"></a>Deklarowanie przestrzeni nazw i przestrzeni nazw elementów członkowskich

Zazwyczaj można zadeklarować przestrzeni nazw w pliku nagłówkowym. Jeśli Twoje implementacji funkcji znajdują się w oddzielnym pliku, kwalifikują się nazwy funkcji, jak w poniższym przykładzie.

```cpp
//contosoData.h
#pragma once
namespace ContosoDataServer
{
    void Foo();
    int Bar();
}
```

Implementacje funkcji w contosodata.cpp należy używać w pełni kwalifikowana nazwa, nawet wtedy, gdy umieścisz **przy użyciu** dyrektywę w górnej części pliku:

```cpp
#include "contosodata.h"
using namespace ContosoDataServer;

void ContosoDataServer::Foo() // use fully-qualified name here
{
   // no qualification needed for Bar()
   Bar();
}

int ContosoDataServer::Bar(){return 0;}
```

Przestrzeń nazw może być zadeklarowana w blokach w jednym pliku, a w wielu plikach. Kompilator tworzy sprzężenie części ze sobą podczas przetwarzania wstępnego, a wynikowy przestrzeń nazw zawiera wszystkie elementy członkowskie zadeklarowana we wszystkich częściach. Na przykład jest obszar nazw std, który jest zadeklarowany w każdym z plików nagłówka w bibliotece standardowej.

Elementy członkowskie przestrzeni nazw o nazwie można zdefiniować poza przestrzenią nazw one zadeklarowane przez jawna kwalifikacja nazwa definiowanego. Jednakże definicja musi znajdować się po punkcie deklaracji w przestrzeni nazw, który zawiera deklarację przestrzeni nazw. Na przykład:

```cpp
// defining_namespace_members.cpp
// C2039 expected
namespace V {
        void f();
    }

    void V::f() { }        // ok
    void V::g() { }        // C2039, g() is not yet a member of V

    namespace V {
        void g();
    }
}
```

Ten błąd może wystąpić, gdy elementów członkowskich przestrzeni nazw są deklarowane w wiele plików nagłówkowych i tych nagłówków nie zostały uwzględnione w odpowiedniej kolejności.

## <a name="the-global-namespace"></a>Globalna przestrzeń nazw

Jeśli identyfikator nie jest zadeklarowany w jawną przestrzeń nazw, jest częścią niejawne globalnej przestrzeni nazw. Ogólnie rzecz biorąc, należy unikać, dzięki czemu deklaracji w zakresie globalnym, jeśli to możliwe, z wyjątkiem punktu wejścia [funkcji main](../c-language/main-function-and-program-execution.md), co jest wymagane w globalnej przestrzeni nazw. Aby kwalifikuj jawnie identyfikator globalny, użyj operatora rozpoznawania zakresu bez nazwy, podobnie jak w `::SomeFunction(x);`. Będzie to odróżnić identyfikator od żadnego elementu o tej samej nazwie w innych nazw, a także pozwoli to uczynić kod łatwiejszym dla innych użytkowników zrozumieć.

## <a name="the-std-namespace"></a>Obszar nazw std

Wszystkie typy biblioteki standardowej języka C++ i funkcje są deklarowane w `std` przestrzeni nazw lub przestrzeni nazw zagnieździć `std`.

## <a name="nested-namespaces"></a>Zagnieżdżone przestrzenie nazw

Przestrzenie nazw mogą być zagnieżdżone. Ma zwykłych zagnieżdżone przestrzenie nazw niekwalifikowanych dostęp do elementów członkowskich jego elementu nadrzędnego, ale elementy nadrzędne bez niekwalifikowanej dostępu do zagnieżdżone przestrzenie nazw (chyba że jest ona zadeklarowana jako wbudowana), jak pokazano w poniższym przykładzie:

```cpp
namespace ContosoDataServer
{
    void Foo();

    namespace Details
    {
        int CountImpl;
        void Ban() { return Foo(); }
    }

    int Bar(){...};
    int Baz(int i) { return Details::CountImpl; }
}
```

Zwykłe zagnieżdżone przestrzenie nazw może służyć do hermetyzacji szczegóły wewnętrznej implementacji, które nie są częścią interfejsu publicznego nadrzędna przestrzeń nazw.

## <a name="inline-namespaces-c-11"></a>Wbudowane przestrzenie nazw (c ++ 11)

W przeciwieństwie do zwykłych zagnieżdżone przestrzenie nazw elementów członkowskich przestrzeni nazw usługi wbudowane są traktowane jako elementy członkowskie nadrzędna przestrzeń nazw. Cecha ta umożliwia wyszukiwanie zależne argumentu funkcji przeciążenia do pracy nad funkcjami, które mają przeciążenia elementu nadrzędnego i zagnieżdżone wbudowane przestrzeni nazw. Umożliwia również zadeklarować specjalizację w nadrzędna przestrzeń nazw dla szablonu, który jest zadeklarowany w przestrzeni nazw wbudowane. W poniższym przykładzie pokazano sposób zewnętrznego kodu tworzy powiązanie z przestrzeni nazw wbudowane domyślnie:

```cpp
//Header.h
#include <string>

namespace Test
{
    namespace old_ns
    {
        std::string Func() { return std::string("Hello from old"); }
    }

    inline namespace new_ns
    {
        std::string Func() { return std::string("Hello from new"); }
    }
}

#include "header.h"
#include <string>
#include <iostream>

int main()
{
    using namespace Test;
    using namespace std;

    string s = Func();
    std::cout << s << std::endl; // "Hello from new"
    return 0;
}
```

Poniższy przykład pokazuje, jak można zadeklarować specjalizację w obiekcie nadrzędnym szablonu, który jest zadeklarowany w przestrzeni nazw wbudowane:

```cpp
namespace Parent
{
    inline namespace new_ns
    {
         template <typename T>
         struct C
         {
             T member;
         };
    }
     template<>
     class C<int> {};
}
```

Wbudowane przestrzenie nazw można użyć jako mechanizm obsługi wersji, zarządzanie zmianami w bibliotece interfejsu publicznego. Na przykład można utworzyć pojedynczy nadrzędna przestrzeń nazw i hermetyzacji każdą wersję interfejsu w jego własnej przestrzeni nazw zagnieżdżone wewnątrz obiektu nadrzędnego. Przestrzeń nazw, która zawiera najbardziej ostatnie lub preferowaną wersję kwalifikuje się jako wbudowane i dlatego jest narażony, tak jakby bezpośrednimi członkami nadrzędna przestrzeń nazw. Kod klienta, który wywołuje Parent::Class będzie automatycznie wiązany nowego kodu. Klienci, którzy wolą używać starszej wersji nadal do niego dostęp przy użyciu w pełni kwalifikowana ścieżka do zagnieżdżone przestrzenie nazw, który ma kod.

Wbudowane — słowo kluczowe musi zostać zastosowana do pierwszej deklaracji przestrzeni nazw w jednostce kompilacji.

Poniższy przykład przedstawia dwie wersje interfejsu, każde WE zagnieżdżone przestrzenie nazw. `v_20` Przestrzeń nazw ma wprowadzając pewne modyfikacje z `v_10` interfejsu i jest oznaczony jako wbudowane. Kod klienta, który używa wywołań i Nowa biblioteka `Contoso::Funcs::Add` wywoła wersji v_20. Kod, który próbuje wywołać `Contoso::Funcs::Divide` uzyskają błąd w czasie kompilacji. Jeśli tak naprawdę potrzebują tej funkcji, mogą uzyskiwać dostęp `v_10` wersji przez jawne wywołanie `Contoso::v_10::Funcs::Divide`.

```cpp
namespace Contoso
{
    namespace v_10
    {
        template <typename T>
        class Funcs
        {
        public:
            Funcs(void);
            T Add(T a, T b);
            T Subtract(T a, T b);
            T Multiply(T a, T b);
            T Divide(T a, T b);
        };
    }

    inline namespace v_20
    {
        template <typename T>
        class Funcs
        {
        public:
            Funcs(void);
            T Add(T a, T b);
            T Subtract(T a, T b);
            T Multiply(T a, T b);
            std::vector<double> Log(double);
            T Accumulate(std::vector<T> nums);
      };
    }
}
```

## <a id="namespace_aliases"></a> Aliasy Namespace

Namespace nazw musi być unikatowa, co oznacza, że często nie powinny być zbyt krótki. Jeśli długość nazwy sprawia, że kod jest trudne do odczytania, lub jest niewygodna do typu w pliku nagłówkowym, których nie można użyć dyrektywy using, a następnie możesz wprowadzić alias przestrzeni nazw, który stanowi skrót od nazwy. Na przykład:

```cpp
namespace a_very_long_namespace_name { class Foo {}; }
namespace AVLNN = a_very_long_namespace_name;
void Bar(AVLNN::Foo foo){ }
```

## <a name="anonymous-or-unnamed-namespaces"></a>anonimowe lub nienazwane przestrzenie nazw

Można utworzyć jawną przestrzeń nazw, ale nie nadaj jej nazwę:

```cpp
namespace
{
    int MyFunc(){}
}
```

Jest to nazywane nienazwane lub anonimowe przestrzeni nazw i jest to przydatne, gdy użytkownik chce ukrywanie deklaracje zmiennych do kodu w innych plikach (czyli ciągowych powiązanie wewnętrzne) bez konieczności tworzenia nazwanego przestrzeni nazw. Cały kod w tym samym pliku widoczne identyfikatorów w przestrzeni nazw usługi bez nazwy, ale identyfikatorów, wraz z przestrzeni nazw, nie są widoczne poza ten plik, lub bardziej precyzyjne poza jednostki translacji.

## <a name="see-also"></a>Zobacz także

[Deklaracje i definicje](declarations-and-definitions-cpp.md)