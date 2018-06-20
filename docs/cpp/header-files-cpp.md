---
title: Pliki nagłówka (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/20/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- header files [C++]
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b571cd2836e66ebef21898af27cf2a6d7082e0e5
ms.sourcegitcommit: d06966efce25c0e66286c8047726ffe743ea6be0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2018
ms.locfileid: "36238760"
---
# <a name="header-files-c"></a>Pliki nagłówka (C++)

Przed użyciem musi być zadeklarowany jako nazwy elementów programu, takich jak zmienne, funkcje, klasy i tak dalej. Na przykład po prostu nie można zapisać `x = 42` bez deklarowania pierwszy "x". 

```cpp
int x; // declaration
x = 42; // use x
```

 Deklaracja informuje kompilator, czy jest **int**, **podwójne**, **funkcja**, **klasy** lub niektóre jeszcze inną czynność.  Ponadto każda nazwa musi być zadeklarowany (bezpośrednio lub pośrednio) w każdym pliku .cpp, w którym jest używana. Podczas kompilowania programu każdego pliku .cpp jest kompilowany niezależnie do jednostki kompilacji. Kompilator nie ma informacji o jakie nazwy są zadeklarowane w innych jednostek kompilacji. Oznacza to, że po zdefiniowaniu klasy lub funkcji lub zmienna globalna, należy podać deklaracji ten element w każdym pliku .cpp dodatkowe, które korzysta z niego. Każda deklaracja ten element musi być dokładnie takie same we wszystkich plikach. Niewielkie niespójności spowoduje, że błędy lub niezamierzone zachowanie, gdy konsolidator próbuje Scal wszystkie jednostki kompilacji w jednym programie.

Aby zminimalizować potencjalne błędy, C++ przyjęła z Konwencją przy użyciu *pliki nagłówkowe* zawierać deklaracje. Możesz wprowadzić deklaracjami w pliku nagłówka, a następnie użyj # dyrektywy include w każdym pliku .cpp lub innego pliku nagłówka wymaga tej deklaracji. #Include dyrektywy kopię pliku nagłówka bezpośrednio w pliku .cpp, przed rozpoczęciem kompilacji. 

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono typowy sposób zadeklarować klasy, a następnie użyć go w innym plikiem źródłowym. Zaczniemy pliku nagłówka **my_class.h**. Zawiera definicję klasy, ale należy pamiętać, że definicja jest niekompletny. Funkcja członkowska `do_something` nie jest zdefiniowana:

```cpp
// my_class.h
namespace N
{
    class my_class
    {
    public:
        void do_something();
    };

}
```

Następnie należy utworzyć plik implementacji (zwykle z .cpp lub podobne rozszerzenia). Firma Microsoft będzie wywoływać my_class.cpp pliku i podaj definicję dla deklaracji elementu członkowskiego. Dodamy `#include` dyrektywy dla pliku "my_class.h", aby przypisać deklaracji my_class wstawione na tym etapie w .cpp plików i firma Microsoft obejmują  **\<iostream >** do ściągnięcia w deklaracji `std::cout`. Należy pamiętać, że cudzysłowy są używane do pliki nagłówkowe, w tym samym katalogu co plik źródłowy, i nawiasy są używane dla nagłówków biblioteki standardowej. Ponadto wiele nagłówków biblioteki standardowej nie mają .h lub inne rozszerzenie pliku.

W pliku implementacji, można opcjonalnie używany **przy użyciu** instrukcji, aby uniknąć konieczności zakwalifikować co informację o "my_class" lub "cout" z "N::" lub "std::".  Nie umieszczaj **przy użyciu** instrukcje w plikach nagłówka!

```cpp
// my_class.cpp
#include "my_class.h" // header in local directory
#include <iostream> // header in standard library

using namespace N;
using namespace std;

void my_class::do_something()
{
    cout << "Doing something!" << endl;
}
```

Teraz możemy użyć `my_class` w innym pliku .cpp. Firma Microsoft #include plik nagłówka, aby kompilator ściąga w deklaracji. Wszystkie potrzeby kompilatora wiedzieć jest my_class tej klasy, która ma funkcji publicznego elementu członkowskiego o nazwie `do_something()`.

```cpp
// my_program.cpp
#include "my_class.h"

using namespace N;

int main()
{
    my_class mc;
    mc.do_something();
    return 0;
}
```

Po zakończeniu kompilator kompilowanie każdego pliku .cpp do plików .obj przekazuje plików .obj do konsolidatora. Gdy konsolidator scala plików obiektów znajdzie dokładnie jedną definicję my_class; znajduje się w pliku obj. w my_class.cpp i kompilacja zakończy się pomyślnie.

## <a name="include-guards"></a>Obejmują osłony

Zwykle, mają pliki nagłówkowe *obejmują guard* lub **#pragma raz** dyrektywy w celu zapewnienia ich do pliku .cpp jednego nie są wstawiane wiele razy. 

my_class.h
#<a name="ifndef-myclassh--include-guard"></a>ifndef MY_CLASS_H / / include guard
#<a name="define-myclassh"></a>Zdefiniuj MY_CLASS_H


przestrzeń nazw N {klasy my_class {publicznego: void do_something();};

}

#<a name="endif--myclassh-"></a>ENDIF / * MY_CLASS_H * /

## <a name="what-to-put-in-a-header-file"></a>Co należy umieścić w pliku nagłówka

Ponieważ plik nagłówka może potencjalnie uwzględnianych wielu plików, nie może zawierać definicji, które mogą prowadzić wiele definicji o takiej samej nazwie. Poniżej są niedozwolone, lub są traktowane jako rozwiązaniem bardzo zły:

- definicje typów wbudowanych w przestrzeni nazw lub zakresie globalnym
- definicje funkcji innych niż inline 
- definicje zmiennych z systemem innym niż stała
- definicje agregacji
- nienazwane przestrzenie nazw
- przy użyciu dyrektyw

Użycie **przy użyciu** dyrektywy nie będzie zawsze powodować błąd, ale może dojść skierowania na problem, ponieważ stwarza przestrzeni nazw w zakresie w każdym pliku .cpp, który bezpośrednio lub pośrednio zawiera nagłówka. 

## <a name="sample-header-file"></a>Przykładowy plik nagłówka

W poniższym przykładzie przedstawiono różne rodzaje deklaracje i definicje, które są dozwolone w pliku nagłówka:

```cpp
#pragma once 
#include <vector> // #include directive
#include <string>

namespace N  // namespace declaration
{

    inline namespace P
    {
        //...
    }

    enum class colors : short { red, blue, purple, azure };


    const double PI = 3.14;  // const and constexpr definitions
    constexpr int MeaningOfLife{ 42 };
    constexpr int get_meaning()
    {
        static_assert(MeaningOfLife == 42, "unexpected!"); // static_assert
        return MeaningOfLife;
    }
    using vstr = std::vector<int>;  // type alias
    extern double d; // extern variable

#define LOG   // macro definition

#ifdef LOG   // conditional compilation directive
    void print_to_log();
#endif


    class my_class   // regular class definition, 
    {                // but no non-inline function definitions

        friend class other_class;
    public:
        void do_something();   // definition in my_class.cpp
        inline void put_value(int i) { vals.push_back(i); } // inline OK

    private:
        vstr vals;
        int i;
    };

    struct RGB
    {
        short r{ 0 };  // member initialization
        short g{ 0 };
        short b{ 0 };
    };

    template <typename T>  // template definition
    class value_store
    {
    public:
        value_store<T>() = default;
        void write_value(T val)
        {
            //... function definition OK in template
        }
    private:
        std::vector<T> vals;
    };

    template <typename T>  // template declaration
    class value_widget;

}
