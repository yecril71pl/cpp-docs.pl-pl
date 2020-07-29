---
title: Pliki nagłówkowe (C++)
ms.date: 12/11/2019
helpviewer_keywords:
- header files [C++]
ms.openlocfilehash: 0b76773b8b7d55645c807588fe41b242df9eea2f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227455"
---
# <a name="header-files-c"></a>Pliki nagłówkowe (C++)

Nazwy elementów programu, takich jak zmienne, funkcje, klasy i tak dalej, muszą być zadeklarowane przed użyciem. Na przykład nie można tylko pisać `x = 42` bez uprzedniego deklarowania "x".

```cpp
int x; // declaration
x = 42; // use x
```

Deklaracja instruuje kompilator, czy element jest, **`int`** a **`double`** , **Funkcja**, a **`class`** lub inne.  Ponadto każda nazwa musi być zadeklarowana (bezpośrednio lub pośrednio) w każdym pliku. cpp, w którym jest używana. Podczas kompilowania programu każdy plik CPP jest kompilowany niezależnie do jednostki kompilacji. Kompilator nie ma informacji o tym, jakie nazwy są zadeklarowane w innych jednostkach kompilacji. Oznacza to, że jeśli zdefiniujesz klasę lub funkcję lub zmienną globalną, musisz podać tę deklarację w każdym dodatkowym pliku. cpp, który go używa. Każda deklaracja tego elementu musi być dokładnie taka sama we wszystkich plikach. Niewielka niespójność spowoduje błędy lub niezamierzone zachowanie, gdy konsolidator próbuje scalić wszystkie jednostki kompilacji w jeden program.

Aby zminimalizować prawdopodobieństwo wystąpienia błędów, język C++ przyjął konwencję używania *plików nagłówkowych* , aby zawierać deklaracje. Należy wprowadzić deklaracje w pliku nagłówkowym, a następnie użyć dyrektywy #include w każdym pliku. cpp lub w innym pliku nagłówkowym, który wymaga tej deklaracji. Dyrektywa #include wstawia kopię pliku nagłówkowego bezpośrednio do pliku. cpp przed kompilacją.

> [!NOTE]
> W programie Visual Studio 2019 funkcja *modułów* c++ 20 została wprowadzona jako udoskonalenie i ostateczne zastąpienie dla plików nagłówkowych. Aby uzyskać więcej informacji, zobacz [Omówienie modułów w języku C++](modules-cpp.md).

## <a name="example"></a>Przykład

Poniższy przykład przedstawia typowy sposób deklarowania klasy, a następnie używania jej w innym pliku źródłowym. Zaczniemy od pliku nagłówkowego `my_class.h` . Zawiera definicję klasy, ale należy pamiętać, że definicja jest niekompletna; `do_something`nie zdefiniowano funkcji składowej:

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

Następnie utwórz plik implementacji (zazwyczaj z rozszerzeniem. cpp lub podobnego rozszerzenia). Wywołajemy plik my_class. cpp i podaj definicję deklaracji elementu członkowskiego. Dodajemy `#include` dyrektywę dla pliku "my_class. h", aby w tym momencie wstawiono my_class deklarację w pliku. cpp, a my dodaliśmy `<iostream>` do pobrania w deklaracji `std::cout` . Należy zauważyć, że cudzysłowy są używane dla plików nagłówkowych w tym samym katalogu, co plik źródłowy, a nawiasy ostre są używane dla nagłówków biblioteki standardowej. Ponadto wiele nagłówków biblioteki standardowej nie ma. h ani żadnego innego rozszerzenia pliku.

W pliku implementacji można opcjonalnie użyć **`using`** instrukcji, aby uniknąć konieczności zakwalifikowania się każdego "my_class" lub "cout" z "N::" lub "std::".  Nie należy umieszczać **`using`** instrukcji w plikach nagłówkowych.

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

Teraz możemy użyć `my_class` innego pliku. cpp. #Include pliku nagłówkowego, aby kompilator ściągał deklarację. Wszystkie kompilatora muszą wiedzieć, że my_class jest klasą, która ma wywołaną publiczną funkcję członkowską `do_something()` .

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

Gdy kompilator zakończy Kompilowanie każdego pliku. cpp do plików. obj, przekazuje pliki. obj do konsolidatora. Gdy konsolidator scala pliki obiektów, znajdzie dokładnie jedną definicję dla my_class; znajduje się w pliku. obj, który został utworzony dla my_class. cpp, a kompilacja powiodła się.

## <a name="include-guards"></a>Dołącz osłony

Zazwyczaj pliki nagłówkowe mają *osłonę include* lub dyrektywę, `#pragma once` Aby upewnić się, że nie są one wstawiane wielokrotnie do jednego pliku. cpp.

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

## <a name="what-to-put-in-a-header-file"></a>Co należy umieścić w pliku nagłówkowym

Ponieważ plik nagłówka może być potencjalnie dołączany przez wiele plików, nie może zawierać definicji, które mogą generować wiele definicji o tej samej nazwie. Następujące elementy nie są dozwolone lub są uznawane za nieszkodliwe:

- Wbudowane definicje typów w przestrzeni nazw lub globalnym zakresie
- definicje funkcji innych niż inline
- Definicje zmiennych innych niż const
- definicje agregacji
- nienazwane przestrzenie nazw
- dyrektywy using

Użycie **`using`** dyrektywy nie musi być przyczyną błędu, ale może być przyczyną problemu, ponieważ powoduje, że przestrzeń nazw ma zakres w każdym pliku CPP, który bezpośrednio lub pośrednio zawiera ten nagłówek.

## <a name="sample-header-file"></a>Przykładowy plik nagłówka

W poniższym przykładzie przedstawiono różne rodzaje deklaracji i definicje, które są dozwolone w pliku nagłówka:

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
