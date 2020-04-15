---
title: Pliki nagłówkowe (C++)
ms.date: 12/11/2019
helpviewer_keywords:
- header files [C++]
ms.openlocfilehash: 4ab6a2b2626cde94f35678bc9ec789b80d493b8f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367231"
---
# <a name="header-files-c"></a>Pliki nagłówkowe (C++)

Nazwy elementów programu, takich jak zmienne, funkcje, klasy i tak dalej, muszą być zadeklarowane, zanim będą mogły być używane. Na przykład nie można po `x = 42` prostu pisać bez uprzedniego zadeklarowania "x".

```cpp
int x; // declaration
x = 42; // use x
```

Deklaracja informuje kompilator, czy element jest **int**, **double**, **funkcja**, **klasy** lub innej rzeczy.  Ponadto każda nazwa musi być zadeklarowana (bezpośrednio lub pośrednio) w każdym pliku .cpp, w którym jest używana. Podczas kompilowania programu każdy plik .cpp jest kompilowany niezależnie w jednostkę kompilacji. Kompilator nie ma wiedzy o tym, jakie nazwy są zadeklarowane w innych jednostkach kompilacji. Oznacza to, że jeśli zdefiniujesz klasę lub funkcję lub zmienną globalną, należy podać deklarację tej rzeczy w każdym dodatkowym pliku .cpp, który go używa. Każda deklaracja tego rzeczy musi być dokładnie identyczna we wszystkich plikach. Niewielka niespójność spowoduje błędy lub niezamierzone zachowanie, gdy konsolidator próbuje scalić wszystkie jednostki kompilacji w jeden program.

Aby zminimalizować ryzyko błędów, C++ przyjęła konwencję używania *plików nagłówka* do zawierania deklaracji. Należy dokonać deklaracji w pliku nagłówka, a następnie użyć dyrektywy #include w każdym pliku cpp lub innego pliku nagłówka, który wymaga tej deklaracji. Dyrektywa #include wstawia kopię pliku nagłówka bezpośrednio do pliku cpp przed kompilacją.

> [!NOTE]
> W programie Visual Studio 2019 funkcja *modułów* języka C++20 jest wprowadzana jako ulepszenie i ewentualne zastąpienie plików nagłówkowych. Aby uzyskać więcej informacji, zobacz [Omówienie modułów w języku C++](modules-cpp.md).

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano typowy sposób deklarowania klasy, a następnie użyć jej w innym pliku źródłowym. Zaczniemy od pliku nagłówka, `my_class.h`. Zawiera definicję klasy, ale należy pamiętać, że definicja jest niekompletna; funkcja `do_something` elementu członkowskiego nie jest zdefiniowana:

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

Następnie utwórz plik implementacji (zazwyczaj z rozszerzeniem .cpp lub podobnym). Wywołamy plik my_class.cpp i podamy definicję deklaracji elementu członkowskiego. Dodajemy `#include` dyrektywę dla pliku "my_class.h", aby deklaracja my_class została wstawiona w tym momencie do `<iostream>` pliku .cpp `std::cout`i dołączamy do wciągania deklaracji dla . Należy zauważyć, że cudzysłowy są używane dla plików nagłówkowych w tym samym katalogu co plik źródłowy, a nawiasy kątowe są używane dla standardowych nagłówków biblioteki. Ponadto wiele standardowych nagłówków biblioteki nie ma .h ani żadnego innego rozszerzenia pliku.

W pliku implementacji możemy opcjonalnie użyć **using** instrukcji, aby uniknąć konieczności kwalifikowania każdej wzmianki o "my_class" lub "cout" z "N::" lub "std::".  Nie umieszczaj **instrukcji w** plikach nagłówkowych!

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

Teraz możemy `my_class` użyć w innym pliku .cpp. Mamy #include pliku nagłówka, tak aby kompilator ściąga w deklaracji. Wszystko kompilator musi wiedzieć, że my_class jest klasą, która `do_something()`ma funkcję publicznego elementu członkowskiego o nazwie .

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

Po zakończeniu kompilowania każdego pliku cpp do plików .obj, przekazuje pliki obj do konsolidatora. Gdy konsolidator scala pliki obiektów znajdzie dokładnie jedną definicję dla my_class; znajduje się w pliku obj wyprodukowanym dla my_class.cpp, a kompilacja powiedzie się.

## <a name="include-guards"></a>Uwzględnij osłony

Zazwyczaj pliki nagłówkowe mają *osłonę dołączaną* lub dyrektywę, `#pragma once` aby upewnić się, że nie są wstawiane wiele razy do pojedynczego pliku cpp.

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

## <a name="what-to-put-in-a-header-file"></a>Co umieścić w pliku nagłówka

Ponieważ plik nagłówka może potencjalnie zostać dołączony przez wiele plików, nie może zawierać definicji, które mogą tworzyć wiele definicji o tej samej nazwie. Następujące są niedozwolone lub są uważane za bardzo złą praktykę:

- wbudowane definicje typów w obszarze nazw lub w zakresie globalnym
- definicje funkcji niewwierających
- definicje zmiennych innych niż const
- definicje zagregowane
- nienazwane przestrzenie nazw
- korzystanie z dyrektyw

Użycie **using** dyrektywy nie musi spowodować błąd, ale może potencjalnie spowodować problem, ponieważ przynosi obszar nazw do zakresu w każdym pliku .cpp, który bezpośrednio lub pośrednio zawiera ten nagłówek.

## <a name="sample-header-file"></a>Przykładowy plik nagłówka

Poniższy przykład przedstawia różne rodzaje deklaracji i definicje, które są dozwolone w pliku nagłówka:

```cpp
// sample.h
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
