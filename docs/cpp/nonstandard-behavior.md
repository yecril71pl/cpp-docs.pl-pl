---
title: Niestandardowe zachowanie
ms.date: 05/06/2019
helpviewer_keywords:
- compatibility and compliance, nonstandard behavior
- Microsoft-specific, compiler behavior
- nonstandard behavior, compliance and compatibility
ms.assetid: a57dea27-dc79-4f64-8a83-017e84841773
ms.openlocfilehash: f31938c78e443bb53a286f79661d86b7a6e9edbc
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87186545"
---
# <a name="nonstandard-behavior"></a>Niestandardowe zachowanie

W poniższych sekcjach wymieniono niektóre miejsca, w których implementacja języka C++ firmy Microsoft nie jest zgodna ze standardem C++. Numery sekcji podane poniżej odnoszą się do numerów sekcji w standardzie C++11 (ISO/IEC 14882:2011(E)).

Lista ograniczeń kompilatora, które różnią się od tych zdefiniowanych w standardzie C++, jest określona w [limitach kompilatora](../cpp/compiler-limits.md).

## <a name="covariant-return-types"></a>Kowariantne typy zwracane

Wirtualne klasy bazowe nie są obsługiwane jako kowariantne typy zwracane, gdy funkcja wirtualna ma zmienną liczbę argumentów. Jest to niezgodne z sekcją 10.3.7 specyfikacji ISO C++. Następujący przykład nie kompiluje się, dając błąd kompilatora [C2688](../error-messages/compiler-errors-2/compiler-error-c2688.md)

```cpp
// CovariantReturn.cpp
class A
{
   virtual A* f(int c, ...);   // remove ...
};

class B : virtual A
{
   B* f(int c, ...);   // C2688 remove ...
};
```

## <a name="binding-nondependent-names-in-templates"></a>Powiązanie nazw niezależnych w szablonach

Kompilator języka Microsoft C++ nie obsługuje obecnie powiązań nazw niezależnych podczas wstępnego analizowania szablonu. Jest to niezgodne z sekcją 14.6.3 specyfikacji ISO C++. Może to powodować wystąpienie przeciążeń zadeklarowanych po szablonie (ale przed wystąpieniem szablonu).

```cpp
#include <iostream>
using namespace std;

namespace N {
   void f(int) { cout << "f(int)" << endl;}
}

template <class T> void g(T) {
    N::f('a');   // calls f(char), should call f(int)
}

namespace N {
    void f(char) { cout << "f(char)" << endl;}
}

int main() {
    g('c');
}
// Output: f(char)
```

## <a name="function-exception-specifiers"></a>Specyfikatory wyjątku w funkcji.

Specyfikatory wyjątków funkcji inne niż `throw()` są analizowane, ale nie są używane. Jest to niezgodne z sekcją 15.4 specyfikacji ISO C++. Na przykład:

```cpp
void f() throw(int); // parsed but not used
void g() throw();    // parsed and used
```

Aby uzyskać więcej informacji dotyczących specyfikacji wyjątków, zobacz [specyfikacje wyjątków](../cpp/exception-specifications-throw-cpp.md).

## <a name="char_traitseof"></a>char_traits::eof()

Standardowe Stany języka C++, które [char_traits:: eof](../standard-library/char-traits-struct.md#eof) nie mogą odpowiadać prawidłowej `char_type` wartości. Kompilator języka Microsoft C++ wymusza to ograniczenie dla typu **`char`** , ale nie dla typu **`wchar_t`** . Jest to niezgodne z wymogami określonymi w tabeli 62 w sekcji 12.1.1 specyfikacji ISO C++. Prezentuje to poniższy przykład.

```cpp
#include <iostream>

int main()
{
    using namespace std;

    char_traits<char>::int_type int2 = char_traits<char>::eof();
    cout << "The eof marker for char_traits<char> is: " << int2 << endl;

    char_traits<wchar_t>::int_type int3 = char_traits<wchar_t>::eof();
    cout << "The eof marker for char_traits<wchar_t> is: " << int3 << endl;
}
```

## <a name="storage-location-of-objects"></a>Lokalizacja przechowywania obiektów

Standard C++ (sekcja 1.8.6) wymaga, aby kompletne obiekty C++ miały unikatową lokalizację przechowywania. Jednak w przypadku oprogramowania Microsoft C++ istnieją przypadki, w których typy bez elementów członkowskich danych współdzielą lokalizację magazynu z innymi typami w okresie istnienia obiektu.
