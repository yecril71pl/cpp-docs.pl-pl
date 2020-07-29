---
title: Przestrzenie nazw (C++)
ms.date: 08/30/2017
f1_keywords:
- namespace_CPP
- using_CPP
helpviewer_keywords:
- namespaces [C++]
ms.assetid: d1a5a9ab-1cad-47e6-a82d-385bb77f4188
ms.openlocfilehash: 234df334a8c385859440175cb9a1aab5b2e26ead
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227299"
---
# <a name="namespaces-c"></a>Przestrzenie nazw (C++)

Przestrzeń nazw jest regionem deklaratywnym, który dostarcza zakres do identyfikatorów (nazwy typów, funkcji, zmiennych itp.). Przestrzenie nazw służą do organizowania kodu w grupy logiczne i zapobiegania kolizjom nazw, które mogą wystąpić zwłaszcza wtedy, gdy baza kodu zawiera wiele bibliotek. Wszystkie identyfikatory w zakresie przestrzeni nazw są widoczne dla siebie bez kwalifikacji. Identyfikatory poza przestrzenią nazw mogą uzyskiwać dostęp do elementów członkowskich przy użyciu w pełni kwalifikowanej nazwy dla każdego identyfikatora, na przykład `std::vector<std::string> vec;` lub w innej [deklaracji using](../cpp/using-declaration.md) dla jednego identyfikatora ( `using std::string` ) lub [dyrektywy using](../cpp/namespaces-cpp.md#using_directives) dla wszystkich identyfikatorów w przestrzeni nazw ( `using namespace std;` ). Kod w plikach nagłówkowych powinien zawsze używać w pełni kwalifikowanej nazwy przestrzeni nazw.

W poniższym przykładzie przedstawiono deklarację przestrzeni nazw i trzy sposoby, w których kod poza obszarem nazw może uzyskać dostęp do swoich członków.

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

Użyj w pełni kwalifikowanej nazwy:

```cpp
ContosoData::ObjectManager mgr;
mgr.DoSomething();
ContosoData::Func(mgr);
```

Użyj deklaracji using, aby przenieść jeden identyfikator do zakresu:

```cpp
using ContosoData::ObjectManager;
ObjectManager mgr;
mgr.DoSomething();
```

Użyj dyrektywy using, aby przenieść wszystkie elementy w przestrzeni nazw do zakresu:

```cpp
using namespace ContosoData;

ObjectManager mgr;
mgr.DoSomething();
Func(mgr);
```

## <a name="using-directives"></a><a id="using_directives"></a>dyrektywy using

**`using`** Dyrektywa zezwala na wszystkie nazwy w, **`namespace`** które mają być używane bez *nazwy przestrzeni nazw* jako jawnego kwalifikatora. Użyj dyrektywy using w pliku implementacji (tj. *. cpp), jeśli używasz kilku różnych identyfikatorów w przestrzeni nazw; Jeśli używasz tylko jednego lub dwóch identyfikatorów, rozważ użycie deklaracji using, aby przenieść te identyfikatory tylko do zakresu, a nie wszystkich identyfikatorów w przestrzeni nazw. Jeśli zmienna lokalna ma taką samą nazwę jak zmienna przestrzeni nazw, zmienna przestrzeni nazw jest ukryta. Błędem jest zmienna przestrzeni nazw o takiej samej nazwie jak zmienna globalna.

> [!NOTE]
> Dyrektywa using może być umieszczona w górnej części pliku. cpp (w zakresie pliku) lub wewnątrz definicji klasy lub funkcji.
>
> Ogólnie rzecz biorąc, Unikaj umieszczania dyrektyw Using w plikach nagłówkowych (*. h), ponieważ każdy plik, który zawiera ten nagłówek, spowoduje przekazanie wszystkiego w przestrzeni nazw, co może spowodować Ukrywanie nazw i kolizję nazw, które są bardzo trudne do debugowania. Zawsze używaj w pełni kwalifikowanych nazw w pliku nagłówkowym. Jeśli te nazwy są zbyt długie, można użyć aliasu przestrzeni nazw, aby je skrócić. (Zobacz poniżej).

## <a name="declaring-namespaces-and-namespace-members"></a>Deklarowanie przestrzeni nazw i elementów członkowskich przestrzeni nazw

Zazwyczaj należy zadeklarować przestrzeń nazw w pliku nagłówkowym. Jeśli implementacje funkcji znajdują się w osobnym pliku, należy zakwalifikować nazwy funkcji, jak w tym przykładzie.

```cpp
//contosoData.h
#pragma once
namespace ContosoDataServer
{
    void Foo();
    int Bar();
}
```

Implementacje funkcji w contosodata. cpp powinny używać w pełni kwalifikowanej nazwy, nawet jeśli w **`using`** górnej części pliku zostanie umieszczona dyrektywa:

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

Przestrzeń nazw może być zadeklarowana w wielu blokach w jednym pliku i w wielu plikach. Kompilator sprzęga części podczas przetwarzania wstępnego, a powstająca przestrzeń nazw zawiera wszystkie elementy członkowskie zadeklarowane we wszystkich częściach. Przykładem jest standardowa przestrzeń nazw, która jest zadeklarowana w każdym z plików nagłówkowych w standardowej bibliotece.

Elementy członkowskie nazwanej przestrzeni nazw można zdefiniować poza przestrzenią nazw, w której są one deklarowane przez jawną kwalifikację zdefiniowanej nazwy. Jednakże definicja musi pojawić się po punkcie deklaracji w przestrzeni nazw, która jest ujęta w przestrzeń nazw deklaracji. Na przykład:

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
```

Ten błąd może wystąpić, gdy elementy członkowskie przestrzeni nazw są zadeklarowane w wielu plikach nagłówkowych, a nagłówki te nie zostały uwzględnione w poprawnej kolejności.

## <a name="the-global-namespace"></a>Globalna przestrzeń nazw

Jeśli identyfikator nie jest zadeklarowany w jawnej przestrzeni nazw, jest częścią niejawnej globalnej przestrzeni nazw. Ogólnie rzecz biorąc, należy unikać tworzenia deklaracji w zakresie globalnym, gdy jest to możliwe, z wyjątkiem [funkcji Main](../c-language/main-function-and-program-execution.md)punktu wejścia, która musi znajdować się w globalnej przestrzeni nazw. Aby jawnie zakwalifikować identyfikator globalny, użyj operatora rozpoznawania zakresu bez nazwy, jak w `::SomeFunction(x);` . Spowoduje to odróżnienie identyfikatora od wszystkich elementów o tej samej nazwie w innej przestrzeni nazw, a także pomoże Ci ułatwić zrozumienie kodu innym użytkownikom.

## <a name="the-std-namespace"></a>Przestrzeń nazw std

Wszystkie typy i funkcje standardowej biblioteki C++ są deklarowane w `std` przestrzeni nazw lub przestrzeni nazw zagnieżdżonych wewnątrz `std` .

## <a name="nested-namespaces"></a>Zagnieżdżone przestrzenie nazw

Przestrzenie nazw mogą być zagnieżdżane. Zwykła zagnieżdżona przestrzeń nazw ma niekwalifikowany dostęp do elementów członkowskich jego elementu nadrzędnego, ale nadrzędne elementy członkowskie nie mają niekwalifikowanego dostępu do zagnieżdżonej przestrzeni nazw (chyba że jest ona zadeklarowana jako wbudowana), jak pokazano w następującym przykładzie:

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

Zwykłe zagnieżdżone przestrzenie nazw mogą być używane do hermetyzacji wewnętrznych szczegółów implementacji, które nie są częścią publicznego interfejsu przestrzeni nazw nadrzędnej.

## <a name="inline-namespaces-c-11"></a>Wbudowane przestrzenie nazw (C++ 11)

W przeciwieństwie do zwykłej zagnieżdżonej przestrzeni nazw, elementy członkowskie wbudowanej przestrzeni nazw są traktowane jako elementy członkowskie nadrzędnej przestrzeni nazw. Ta cecha włącza wyszukiwanie zależne od argumentów dla przeciążonych funkcji do pracy z funkcjami, które mają przeciążenia w nadrzędnej i zagnieżdżonej wbudowanej przestrzeni nazw. Umożliwia także zadeklarować specjalizację w nadrzędnej przestrzeni nazw szablonu, który jest zadeklarowany w wbudowanej przestrzeni nazw. Poniższy przykład pokazuje, jak kod zewnętrzny jest domyślnie powiązany z wbudowaną przestrzenią nazw:

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

Poniższy przykład pokazuje, jak można zadeklarować specjalizację w elemencie nadrzędnym szablonu, który jest zadeklarowany w wbudowanej przestrzeni nazw:

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

Aby zarządzać zmianami interfejsu publicznego biblioteki programu, można użyć wbudowanych przestrzeni nazw jako mechanizmu obsługi wersji. Na przykład można utworzyć pojedynczą przestrzeń nazw nadrzędną i hermetyzować poszczególne wersje interfejsu we własnym obszarze nazw zagnieżdżonych w elemencie nadrzędnym. Przestrzeń nazw, która zawiera najnowszą lub preferowaną wersję, jest kwalifikowana jako wbudowana i dlatego jest udostępniana tak, jakby była bezpośrednią składową nadrzędnej przestrzeni nazw. Kod klienta, który wywołuje element nadrzędny:: Class, zostanie automatycznie powiązany z nowym kodem. Klienci, którzy wolą używać starszej wersji, mogą nadal uzyskać do niej dostęp przy użyciu w pełni kwalifikowanej ścieżki do zagnieżdżonej przestrzeni nazw, która ma ten kod.

Wbudowane słowo kluczowe musi być stosowane do pierwszej deklaracji przestrzeni nazw w jednostce kompilacji.

Poniższy przykład przedstawia dwie wersje interfejsu, każdy w zagnieżdżonej przestrzeni nazw. `v_20`Przestrzeń nazw ma pewne modyfikacje w `v_10` interfejsie i jest oznaczona jako wbudowana. Kod klienta korzystający z nowej biblioteki i wywołań wywoła `Contoso::Funcs::Add` wersję v_20. Kod, który próbuje wywołać, `Contoso::Funcs::Divide` spowoduje teraz błąd czasu kompilacji. Jeśli naprawdę potrzebują tej funkcji, nadal mogą uzyskać dostęp do `v_10` wersji przez jawne wywołanie `Contoso::v_10::Funcs::Divide` .

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

## <a name="namespace-aliases"></a><a id="namespace_aliases"></a>Aliasy przestrzeni nazw

Nazwy przestrzeni nazw muszą być unikatowe, co oznacza, że często nie powinny być za krótkie. Jeśli długość nazwy utrudnia odczytywanie kodu lub żmudnym do wpisywania w pliku nagłówkowym, gdzie nie można użyć dyrektyw, można utworzyć alias przestrzeni nazw, który służy jako skrót dla rzeczywistej nazwy. Na przykład:

```cpp
namespace a_very_long_namespace_name { class Foo {}; }
namespace AVLNN = a_very_long_namespace_name;
void Bar(AVLNN::Foo foo){ }
```

## <a name="anonymous-or-unnamed-namespaces"></a>anonimowe lub nienazwane przestrzenie nazw

Można utworzyć jawną przestrzeń nazw, ale nie nadać jej nazwy:

```cpp
namespace
{
    int MyFunc(){}
}
```

Jest to nazywane nienazwanymi lub anonimowymi przestrzeniami nazw i jest przydatne, gdy chcesz, aby deklaracje zmiennych były niewidoczne w kodzie w innych plikach (tj. powiązać wewnętrzne powiązania) bez konieczności tworzenia nazwanego obszaru nazw. Cały kod w tym samym pliku może zobaczyć identyfikatory w nienazwanym obszarze nazw, ale identyfikatory, wraz z samą przestrzenią nazw, nie są widoczne poza tym plikiem — lub dokładniej poza jednostką tłumaczenia.

## <a name="see-also"></a>Zobacz także

[Deklaracje i definicje](declarations-and-definitions-cpp.md)
