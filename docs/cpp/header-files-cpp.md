---
title: Pliki nagłówków (C++) | Dokumentacja firmy Microsoft
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
ms.workload:
- cplusplus
ms.openlocfilehash: 7d1e477b04421f7e8920bba47b2eba4e73df34cb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46028535"
---
# <a name="header-files-c"></a>Pliki nagłówków (C++)

Muszą być zadeklarowane nazwy elementów programu, takie jak zmienne, funkcje, klasy i tak dalej, zanim będzie można ich użyć. Na przykład, po prostu nie można zapisywać `x = 42` bez pierwszy deklarowania "x".

```cpp
int x; // declaration
x = 42; // use x
```

Deklaracja informuje kompilator, czy jest **int**, **double**, **funkcja**, **klasy** lub coś innego.  Ponadto każda nazwa musi być zadeklarowany (bezpośrednio lub pośrednio) w każdym pliku .cpp, w którym jest używany. Gdy kompilujesz program, każdy plik .cpp jest skompilowany niezależnie do jednostki kompilacji. Kompilator nie ma informacji o jakie nazwy są deklarowane w innych jednostkach kompilacji. Oznacza to, że po zdefiniowaniu klasy lub funkcji lub zmienna globalna, należy podać deklarację to coś w każdym pliku .cpp dodatkowe, które go używa. Każda deklaracja to coś musi być dokładnie takie same we wszystkich plikach. Nieznaczne niespójności spowoduje, że błędy lub niezamierzone zachowanie, gdy próbuje Scal wszystkie jednostki kompilacji w jeden program łączący.

Aby zminimalizować ryzyko błędów, C++ przyjął Konwencji przy użyciu *pliki nagłówkowe* zawierać deklaracje. Możesz wprowadzić deklaracji w pliku nagłówkowym, a następnie użyj # dyrektywy include w każdym pliku .cpp lub inny plik nagłówka wymaga tej deklaracji. #Include dyrektywy kopię pliku nagłówka bezpośrednio do pliku .cpp, przed rozpoczęciem kompilacji.

## <a name="example"></a>Przykład

Poniższy przykład przedstawia typową metodą zadeklarować klasy, a następnie używania jej w innym plikiem źródłowym. Rozpoczniemy od pliku nagłówka `my_class.h`. Zawiera definicję klasy, ale należy pamiętać, że definicja jest niekompletny. Funkcja elementu członkowskiego `do_something` nie jest zdefiniowany:

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

Następnie należy utworzyć plik implementacji (zazwyczaj z .cpp lub podobne rozszerzenia). Utworzymy wywołać my_class.cpp pliku i podać definicję dla deklaracji elementu członkowskiego. Dodamy `#include` dyrektywy dla pliku "my_class.h", aby mogła mieć deklaracji my_class wstawione w tym momencie w .cpp pliku, a firma Microsoft obejmują `<iostream>` do ściągania w deklaracji pod kątem `std::cout`. Należy pamiętać, że cudzysłowy są używane do plików nagłówkowych w tym samym katalogu co plik źródłowy i nawiasy są używane dla nagłówków biblioteki standardowej. Ponadto wiele nagłówków biblioteki standardowej ma .h lub inne rozszerzenie pliku.

W pliku implementacji możemy opcjonalnie użyć **przy użyciu** instrukcję, aby uniknąć kwalifikowania co wzmiankę "my_class" lub "cout" z "N::" lub "std::".  Nie umieszczaj **przy użyciu** instrukcji w pliki nagłówkowe!

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

Teraz możemy użyć `my_class` w innym pliku .cpp. Firma Microsoft #include plik nagłówka, aby kompilator ściąga w deklaracji. Wszystkie potrzeby kompilatora wiedzieć, jest my_class tej klasy, która ma funkcję publicznego elementu członkowskiego o nazwie `do_something()`.

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

Po zakończeniu kompilowania każdy plik .cpp do plików .obj kompilator przekazuje pliki .obj do konsolidatora. Gdy konsolidator Scala pliki obiektów znajdzie dokładnie jedną definicję my_class; znajduje się w pliku .obj, generowany dla my_class.cpp, a kompilacja zakończy się pomyślnie.

## <a name="include-guards"></a>Obejmują osłony

Zazwyczaj mają pliki nagłówkowe *obejmują guard* lub `#pragma once` dyrektywy w celu zapewnienia ich do pliku .cpp pojedynczej nie są wstawiane wiele razy.

```cpp
// my_class.h
#ifndef MY_CLASS_H // include guard
#define MY_CLASS_H

namespace N
{
    class my_class
    {
    public:
        void do_something();
    };
}

#endif /* MY_CLASS_H */
```

## <a name="what-to-put-in-a-header-file"></a>Co należy umieścić w pliku nagłówka

Ponieważ plik nagłówkowy potencjalnie mogą zostać dołączone przez wiele plików, nie może zawierać definicje, które może tworzyć wiele definicji o takiej samej nazwie. Poniżej są niedozwolone lub są uważane za bardzo złym zwyczajem:

- Definicje typu wbudowanego w przestrzeni nazw lub zasięgu globalnym
- definicje funkcji innych niż inline
- definicje zmiennych wartości innej niż stała
- definicje agregacji
- nienazwane przestrzenie nazw
- dyrektywy Using

Korzystanie z **przy użyciu** dyrektywy niekoniecznie nie będzie powodował błąd, ale może potencjalnie spowodować problem, ponieważ zapewnia przestrzeń nazw do zakresu w każdym pliku .cpp, który bezpośrednio lub pośrednio zawiera nagłówka.

## <a name="sample-header-file"></a>Przykładowy plik nagłówka

Poniższy przykład pokazuje różne rodzaje deklaracje i definicje, które są dozwolone w pliku nagłówka:

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
```