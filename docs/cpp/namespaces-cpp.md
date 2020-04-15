---
title: Przestrzenie nazw (C++)
ms.date: 08/30/2017
f1_keywords:
- namespace_CPP
- using_CPP
helpviewer_keywords:
- namespaces [C++]
ms.assetid: d1a5a9ab-1cad-47e6-a82d-385bb77f4188
ms.openlocfilehash: 4957ec5a5face860d2e39861eddc8f7e5abe9370
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367914"
---
# <a name="namespaces-c"></a>Przestrzenie nazw (C++)

Obszar nazw jest regionem deklaratywnym, który udostępnia zakres identyfikatorów (nazwy typów, funkcji, zmiennych itp.) wewnątrz niego. Przestrzenie nazw są używane do organizowania kodu w grupy logiczne i aby zapobiec kolizji nazw, które mogą wystąpić, zwłaszcza gdy baza kodu zawiera wiele bibliotek. Wszystkie identyfikatory w zakresie obszaru nazw są widoczne dla siebie bez kwalifikacji. Identyfikatory poza obszarem nazw mogą uzyskiwać dostęp do elementów `std::vector<std::string> vec;`członkowskich przy użyciu w pełni kwalifikowanej`using std::string`nazwy dla każdego identyfikatora, na przykład, albo przez using [Declaration](../cpp/using-declaration.md) for a single identifier ( ) lub [za pomocą dyrektywy](../cpp/namespaces-cpp.md#using_directives) dla wszystkich identyfikatorów w obszarze nazw (`using namespace std;`). Kod w plikach nagłówkowych należy zawsze używać w pełni kwalifikowanej nazwy obszaru nazw.

W poniższym przykładzie przedstawiono deklarację obszaru nazw i trzy sposoby, że kod poza obszarem nazw może uzyskać dostęp do swoich członków.

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

Użyj using deklaracji, aby wprowadzić jeden identyfikator do zakresu:

```cpp
using ContosoData::ObjectManager;
ObjectManager mgr;
mgr.DoSomething();
```

Użyj using dyrektywy, aby wprowadzić wszystko w obszarze nazw do zakresu:

```cpp
using namespace ContosoData;

ObjectManager mgr;
mgr.DoSomething();
Func(mgr);
```

## <a name="using-directives"></a><a id="using_directives"></a>korzystanie z dyrektyw

Using **using** Dyrektywy umożliwia wszystkie nazwy w **obszarze nazw,** które mają być używane bez *namespace* jako jawne kwalifikator. Użyj using dyrektywy w pliku implementacji (tj. *.cpp), jeśli używasz kilku różnych identyfikatorów w obszarze nazw; Jeśli używasz tylko jednego lub dwóch identyfikatorów, należy wziąć pod uwagę using deklaracji tylko przenieść te identyfikatory do zakresu, a nie wszystkie identyfikatory w obszarze nazw. Jeśli zmienna lokalna ma taką samą nazwę jak zmienna obszaru nazw, zmienna obszaru nazw jest ukryta. Jest to błąd, aby mieć zmienną przestrzeni nazw o takiej samej nazwie jak zmienna globalna.

> [!NOTE]
> A using dyrektywy mogą być umieszczone w górnej części pliku .cpp (w zakresie pliku) lub wewnątrz definicji klasy lub funkcji.
>
> Ogólnie rzecz biorąc należy unikać umieszczania przy użyciu dyrektyw w plikach nagłówka (*.h), ponieważ każdy plik, który zawiera ten nagłówek spowoduje, że wszystko w obszarze nazw do zakresu, co może spowodować ukrywanie nazw i problemy z kolizją nazw, które są bardzo trudne do debugowania. Zawsze używaj w pełni kwalifikowanych nazw w pliku nagłówka. Jeśli te nazwy są zbyt długie, można użyć aliasu obszaru nazw, aby je skrócić. (Patrz poniżej).

## <a name="declaring-namespaces-and-namespace-members"></a>Deklarowanie obszarów nazw i elementów członkowskich obszaru nazw

Zazwyczaj deklarujesz obszar nazw w pliku nagłówka. Jeśli implementacje funkcji znajdują się w oddzielnym pliku, następnie kwalifikuj nazwy funkcji, jak w tym przykładzie.

```cpp
//contosoData.h
#pragma once
namespace ContosoDataServer
{
    void Foo();
    int Bar();
}
```

Implementacje funkcji w contosodata.cpp powinny używać w pełni kwalifikowanej nazwy, nawet jeśli **u** góry pliku umieścisz używaną dyrektywę:

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

Obszar nazw można zadeklarować w wielu blokach w jednym pliku i w wielu plikach. Kompilator łączy części razem podczas przetwarzania wstępnego i wynikowy obszar nazw zawiera wszystkie elementy członkowskie zadeklarowane we wszystkich częściach. Przykładem tego jest obszar nazw std, który jest zadeklarowany w każdym z plików nagłówkowych w bibliotece standardowej.

Elementy członkowskie nazwanego obszaru nazw można zdefiniować poza obszarem nazw, w którym są deklarowane przez jawną kwalifikację zdefiniowanej nazwy. Jednak definicja musi pojawić się po punkcie deklaracji w obszarze nazw, który otacza obszar nazw deklaracji. Przykład:

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

Ten błąd może wystąpić, gdy elementy członkowskie obszaru nazw są zadeklarowane w wielu plikach nagłówkowych i nie zostały uwzględnione te nagłówki w odpowiedniej kolejności.

## <a name="the-global-namespace"></a>Globalna przestrzeń nazw

Jeśli identyfikator nie jest zadeklarowany w jawnym obszarze nazw, jest częścią niejawnej globalnej przestrzeni nazw. Ogólnie rzecz biorąc, należy unikać dokonywania deklaracji w zakresie globalnym, jeśli to możliwe, z wyjątkiem punktu wejścia [głównego funkcji](../c-language/main-function-and-program-execution.md), który jest wymagany do w globalnej przestrzeni nazw. Aby jawnie zakwalifikować identyfikator globalny, użyj operatora rozpoznawania zakresu `::SomeFunction(x);`bez nazwy, jak w . Spowoduje to odróżnienie identyfikatora od wszystkiego o tej samej nazwie w dowolnym innym obszarze nazw, a także ułatwi zrozumienie kodu innym osobom.

## <a name="the-std-namespace"></a>Obszar nazw std

Wszystkie standardowe typy i funkcje biblioteki C++ są deklarowane w obszarze `std` nazw lub przestrzeniach nazw zagnieżdżonych wewnątrz `std`.

## <a name="nested-namespaces"></a>Zagnieżdżone przestrzenie nazw

Przestrzenie nazw mogą być zagnieżdżone. Zwykły zagnieżdżony obszar nazw ma niezakwalifikowany dostęp do członków nadrzędnych, ale członkowie nadrzędny nie mają niekwalifikowanego dostępu do zagnieżdżonego obszaru nazw (chyba że jest zadeklarowany jako wbudowany), jak pokazano w poniższym przykładzie:

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

Zwykłe zagnieżdżone przestrzenie nazw mogą służyć do hermetyzacji szczegółów implementacji wewnętrznej, które nie są częścią interfejsu publicznego nadrzędnego obszaru nazw.

## <a name="inline-namespaces-c-11"></a>Wbudowane przestrzenie nazw (C++ 11)

W przeciwieństwie do zwykłej zagnieżdżonej przestrzeni nazw elementy członkowskie wbudowanej przestrzeni nazw są traktowane jako elementy członkowskie nadrzędnego obszaru nazw. Ta cecha umożliwia wyszukiwanie zależne od argumentów nad przeciążonymi funkcjami do pracy nad funkcjami, które mają przeciążenia w chłodzieniu i zagnieżdżonej wbudowanej przestrzeni nazw. Umożliwia również zadeklarowanie specjalizacji w nadrzędnej przestrzeni nazw dla szablonu zadeklarowanego w wbudowanym obszarze nazw. W poniższym przykładzie pokazano, jak domyślnie powiązanie kodu zewnętrznego z wbudowanym obszarem nazw:

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

W poniższym przykładzie pokazano, jak można zadeklarować specjalizację w czuciu szablonu zadeklarowanego w wbudowanej przestrzeni nazw:

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

Wbudowane przestrzenie nazw można używać jako mechanizmu przechowywania wersji do zarządzania zmianami w interfejsie publicznym biblioteki. Na przykład można utworzyć pojedynczy nadrzędny obszar nazw i hermetyzować każdą wersję interfejsu we własnym obszarze nazw zagnieżdżonego wewnątrz nadrzędnego. Obszar nazw, który zawiera najnowszą lub preferowaną wersję jest kwalifikowany jako wbudowany i dlatego jest narażony tak, jakby był bezpośrednim członkiem nadrzędnego obszaru nazw. Kod klienta, który wywołuje Parent::Class automatycznie powiązać z nowym kodem. Klienci, którzy wolą używać starszej wersji, nadal mogą uzyskać do niej dostęp przy użyciu w pełni kwalifikowanej ścieżki do zagnieżdżonej przestrzeni nazw, która ma ten kod.

Wbudowane słowo kluczowe musi być stosowane do pierwszej deklaracji obszaru nazw w jednostce kompilacji.

W poniższym przykładzie przedstawiono dwie wersje interfejsu, każda w zagnieżdżonej przestrzeni nazw. Obszar `v_20` nazw ma pewne `v_10` modyfikacje z interfejsu i jest oznaczony jako wbudowany. Kod klienta, który używa nowej `Contoso::Funcs::Add` biblioteki i wywołań wywoła v_20 wersji. Kod, który `Contoso::Funcs::Divide` próbuje wywołać, teraz otrzymasz błąd czasu kompilacji. Jeśli naprawdę potrzebują tej funkcji, nadal `v_10` mogą uzyskać `Contoso::v_10::Funcs::Divide`dostęp do wersji, wyraźnie wywołując .

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

## <a name="namespace-aliases"></a><a id="namespace_aliases"></a>Aliasy obszaru nazw

Nazwy obszaru nazw muszą być unikatowe, co oznacza, że często nie powinny być zbyt krótkie. Jeśli długość nazwy sprawia, że kod jest trudny do odczytania lub jest nużące wpisywać w pliku nagłówka, w którym nie można używać dyrektyw, można wprowadzić alias obszaru nazw, który służy jako skrót dla rzeczywistej nazwy. Przykład:

```cpp
namespace a_very_long_namespace_name { class Foo {}; }
namespace AVLNN = a_very_long_namespace_name;
void Bar(AVLNN::Foo foo){ }
```

## <a name="anonymous-or-unnamed-namespaces"></a>anonimowe lub nienazwane przestrzenie nazw

Można utworzyć jawny obszar nazw, ale nie nadać mu nazwy:

```cpp
namespace
{
    int MyFunc(){}
}
```

Jest to nazywane nienazwany lub anonimowy obszar nazw i jest to przydatne, gdy chcesz, aby deklaracje zmiennych niewidoczne dla kodu w innych plikach (tj. dać im wewnętrzne powiązania) bez konieczności tworzenia nazwanego obszaru nazw. Cały kod w tym samym pliku może zobaczyć identyfikatory w nienazwanej przestrzeni nazw, ale identyfikatory wraz z samą przestrzenią nazw nie są widoczne poza tym plikiem, a dokładniej poza jednostką tłumaczenia.

## <a name="see-also"></a>Zobacz też

[Deklaracje i definicje](declarations-and-definitions-cpp.md)
