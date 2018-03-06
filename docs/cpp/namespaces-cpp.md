---
title: Przestrzenie nazw (C++) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 08/30/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- namespace_CPP
- using_CPP
dev_langs:
- C++
helpviewer_keywords:
- namespaces [C++], C++
- namespaces [C++]
- namespaces [C++], global
- global namespace
- Visual C++, namespaces
ms.assetid: d1a5a9ab-1cad-47e6-a82d-385bb77f4188
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 801bd8ee8e81c0126ae88c1fb9213b25b9f103dd
ms.sourcegitcommit: 4e01d36ffa64ea11bacf589f79d2f1df947e2510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2018
---
# <a name="namespaces-c"></a>Przestrzenie nazw (C++)
Przestrzeń nazw jest deklaratywne region, który zawiera zakres identyfikatorów (nazwy typów, funkcji, zmienne, itp.) w nim. Przestrzenie nazw są używane do organizowania kodu w logiczne grupy i aby uniknąć konfliktów nazw, które mogą wystąpić, szczególnie w przypadku, gdy kodzie zawiera wiele bibliotek. Wszystkie identyfikatory w zakresie przestrzeni nazw są widoczne dla siebie bez kwalifikacji. Identyfikatory poza obszar nazw mogą uzyskiwać dostęp do elementów członkowskich przy użyciu w pełni kwalifikowanej nazwy dla każdego identyfikatora, na przykład `std::vector<std::string> vec;`, w przeciwnym razie przez [za pomocą deklaracji](../cpp/using-declaration.md) dla jednego identyfikatora (`using std::string`), lub [dyrektywa using](../cpp/namespaces-cpp.md#using_directives) dla wszystkich identyfikatorów w przestrzeni nazw (`using namespace std;`). Kod w nagłówku plików zawsze należy używać przestrzeni nazw w pełni kwalifikowanej nazwy.  
  
 W poniższym przykładzie przedstawiono deklaracja przestrzeni nazw i trzy sposoby, które kodu poza przestrzeni nazw można uzyskuje dostęp do ich elementy członkowskie.  
  
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
  
 Użyj używającego deklaracji wprowadzenia jednego identyfikatora w zakresie:  
  
```cpp  
using ContosoData::ObjectManager;  
ObjectManager mgr;  
mgr.DoSomething();  
  
```  
  
 Użyj using dyrektywa, aby wyświetlić wszystkie elementy w przestrzeni nazw w zakresie:  
  
```cpp  
using namespace ContosoData;
  
ObjectManager mgr;  
mgr.DoSomething();  
Func(mgr);  
  
```  
  
## <a id="using_directives"></a> przy użyciu dyrektyw  
 `using` Dyrektywy umożliwia wszystkich nazw w **przestrzeni nazw** ma być używany bez *nazwę przestrzeni nazw* jako jawne kwalifikatora. Użyj using dyrektywy w pliku z implementacją (tj. *.cpp), jeśli używasz kilku różnych identyfikatorów, w obszarze nazw; Jeśli używane są tylko jeden lub dwa identyfikatory, należy rozważyć użycie deklaracji tylko wprowadzenia tych identyfikatorów w zakresie, a nie wszystkie identyfikatory w przestrzeni nazw. Jeśli zmienna lokalna ma taką samą nazwę jak zmienna przestrzeni nazw, zmienna przestrzeni nazw jest ukryty. Jest błąd, aby mieć zmienna o takiej samej nazwie jako zmiennej globalnej przestrzeni nazw.  
  
> [!NOTE]
>  Using — dyrektywa można umieścić na początku pliku .cpp (w zakresie pliku), lub wewnątrz definicji klasy lub funkcji.  
>   
>  Ogólnie rzecz biorąc, należy unikać umieszczania przy użyciu dyrektyw w nagłówku pliki (* .h) ponieważ każdego pliku, który zawiera ten nagłówek zostanie wyświetlone wszystkie elementy w przestrzeni nazw w zakresie, co może spowodować, że nazwa ukrywanie i problemów kolizji nazw, które są bardzo trudne do debugowania. Zawsze należy używać w pełni kwalifikowane nazwy w pliku nagłówka. Jeśli tych nazw zbyt długo, można użyć aliasu przestrzeni nazw skrócić je. (Zobacz poniżej).  
  
## <a name="declaring-namespaces-and-namespace-members"></a>Deklarowanie przestrzeni nazw i przestrzeni nazw elementów członkowskich  
 Zazwyczaj można zadeklarować przestrzeni nazw w pliku nagłówka. Jeśli Twoje implementacji funkcji w osobnym pliku, kwalifikują się nazwy funkcji, jak w poniższym przykładzie.  
  
```cpp  
//contosoData.h   
#pragma once  
namespace ContosoDataServer  
{  
    void Foo();  
    int Bar();  
  
}  
```  
  
 Implementacje funkcji w contosodata.cpp należy używać nazwę FQDN, nawet jeśli zostanie `using` dyrektywy w górnej części pliku:  
  
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
  
 Przestrzeń nazw mogą być deklarowane w wielu bloków w jednym pliku, a w wielu plikach. Kompilator przyłączy części razem podczas przetwarzania wstępnego i wynikowy przestrzeń nazw zawiera wszystkich elementów członkowskich zadeklarowanych w wszystkie części. Na przykład jest obszar nazw std, który został zadeklarowany w każdym pliki nagłówków w standardowej bibliotece.  
  
 Poza przestrzeni nazw, w której zostały zgłoszone przez jawna kwalifikacja nazwę definiowanego można zdefiniować elementów członkowskich o nazwie przestrzeni nazw. Jednak definicji musi występować po punkcie deklaracji w przestrzeni nazw, która obejmuje deklaracji przestrzeni nazw. Na przykład:  
  
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
  
 Ten błąd może wystąpić, gdy elementów członkowskich przestrzeni nazw został zadeklarowany w wielu pliki nagłówkowe, a tych nagłówków nie zostały uwzględnione w odpowiedniej kolejności.  
  
## <a name="the-global-namespace"></a>Globalna przestrzeń nazw  
 Jeśli identyfikator nie jest zadeklarowana w jawnej przestrzeni nazw, jest częścią niejawne globalnej przestrzeni nazw. Ogólnie rzecz biorąc, spróbuj unikać wprowadzania deklaracji w zakresie globalnym, jeśli to możliwe, z wyjątkiem punktu wejścia [główna funkcja](../c-language/main-function-and-program-execution.md), który musi być w globalnej przestrzeni nazw. Aby zakwalifikować jawnie identyfikator globalny, użyj operator rozpoznawania zakresów bez nazwy jako w `::SomeFunction(x);`. Spowoduje to rozróżnianie identyfikator od żadnego elementu o takiej samej nazwie w innych nazw i pomoże aby ułatwić użytkownikom zrozumienie kodu.  
  
## <a name="the-std-namespace"></a>Obszar nazw std  
 Wszystkie typy standardowa biblioteka języka C++ i funkcji, które są zadeklarowane w `std` przestrzeni nazw lub przestrzeni nazw zagnieżdżona `std`.  
  
## <a name="nested-namespaces"></a>Zagnieżdżone przestrzenie nazw  
 Przestrzenie nazw mogą być zagnieżdżone. Ma zwykłych zagnieżdżonych przestrzeni nazw niekwalifikowanych dostęp do elementów członkowskich elementu nadrzędnego, ale elementy nadrzędne nie mają niekwalifikowane dostępu do zagnieżdżonych przestrzeni nazw (chyba że jest on zadeklarowany jako wbudowany), jak pokazano w poniższym przykładzie:  
  
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
  
 Zwykłe zagnieżdżonych obszarów nazw umożliwia Hermetyzowanie szczegóły implementacji wewnętrzne, które nie są częścią interfejs publiczny nadrzędną przestrzeń nazw.  
  
## <a name="inline-namespaces-c-11"></a>Przestrzenie nazw wbudowanego (C++ 11)  
 W przeciwieństwie do zwykłych zagnieżdżonych przestrzeni nazw elementów członkowskich przestrzeni nazw w tekście są traktowane jako członkowie nadrzędną przestrzeń nazw. Tej właściwości umożliwia odnośników zależnych argumentu funkcji przeciążenia do pracy w funkcje, które mają przeciążenia w zagnieżdżonych wbudowanego obszaru nazw i nadrzędnym. Umożliwia również deklarować specjalizacji w nadrzędną przestrzeń nazw dla szablonu, który jest zadeklarowana w przestrzeni nazw w tekście. W poniższym przykładzie przedstawiono sposób zewnętrznego kodu wiąże się z obszarem nazw wbudowanego domyślnie:  
  
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
  
 W poniższym przykładzie pokazano, jak można zadeklarować specjalizacji w katalogu nadrzędnym szablonu, który jest zadeklarowana w przestrzeni nazw wbudowany:  
  
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
  
 Przestrzenie nazw w tekście jako mechanizm przechowywanie wersji służy do zarządzania zmianami do publicznego interfejsu biblioteki. Na przykład można utworzyć nadrzędnego pojedynczego obszaru nazw i Hermetyzowanie każdej wersji interfejsu w jego własnej przestrzeni nazw zagnieżdżone wewnątrz obiektu nadrzędnego. Przestrzeni nazw, która zawiera wersję najbardziej ostatnie lub preferowany jest kwalifikowany jako inline, a w związku z tym jest uwidaczniana, tak jakby był on członkiem bezpośredniego nadrzędną przestrzeń nazw. Kod klienta, który wywołuje Parent::Class będzie automatycznie wiązane z nowego kodu. Klienci, którzy wolą używać starszej wersji nadal do niego dostęp przy użyciu w pełni kwalifikowana ścieżka do zagnieżdżonych przestrzeni nazw, która ma ten kod.  
  
 Słowo kluczowe inline musi zostać zastosowana do pierwszej deklaracji przestrzeni nazw w jednostkach kompilacji.  
  
 W poniższym przykładzie przedstawiono dwie wersje interfejsu, każdej z nich w zagnieżdżonych przestrzeni nazw. `v_20` Przestrzeń nazw ma pewne zmiany z `v_10` interfejsu i jest oznaczony jako śródwierszowej. Kod klienta, który korzysta z nowej biblioteki i wywołania `Contoso::Funcs::Add` wywoła v_20 wersji. Kod, który próbuje wywołać `Contoso::Funcs::Divide` uzyskają błąd w czasie kompilacji. Jeśli naprawdę potrzebują tej funkcji, można nadal dostęp `v_10` wersji jawnie wywołując `Contoso::v_10::Funcs::Divide`.  
  
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
 Namespace nazw musi być unikatowa, co oznacza, że często nie powinny być zbyt krótki. Jeśli długość nazwy powoduje, że kod jest trudne do odczytu, lub jest niewygodne typu w pliku nagłówka, której nie można użyć dyrektyw using, a następnie możesz wprowadzić alias przestrzeni nazw, który stanowi skrót od rzeczywistej nazwy. Na przykład:  
  
```cpp  
namespace a_very_long_namespace_name { class Foo {}; }  
namespace AVLNN = a_very_long_namespace_name;  
void Bar(AVLNN::Foo foo){ }  
  
```  
  
## <a name="anonymous-or-unnamed-namespaces"></a>anonimowe lub nienazwanej przestrzeni nazw  
 Można utworzyć jawnej przestrzeni nazw, ale nie nadaj mu nazwę:  
  
```cpp  
namespace  
{  
    int MyFunc(){}  
}  
```  
  
 Ta metoda jest wywoływana bez nazwy lub anonimowe przestrzeni nazw i jest przydatna, jeśli chcesz utworzyć deklaracji zmiennych niewidoczne dla kodu w innych plikach (tj. Nadaj im zewnętrzne) bez konieczności tworzenia nazwanych przestrzeni nazw. Cały kod w tym samym pliku widoczne identyfikatory w nienazwanej przestrzeni nazw, ale identyfikatorów, wraz z przestrzeni nazw, nie są widoczne poza tego pliku — lub bardziej precyzyjnie poza jednostce tłumaczenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Deklaracje i definicje](declarations-and-definitions-cpp.md)
