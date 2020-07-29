---
title: /Zc:implicitNoexcept (niejawne specyfikatory wyjątków)
ms.date: 03/06/2018
f1_keywords:
- /Zc:implicitNoexcept
helpviewer_keywords:
- /Zc:implicitNoexcept
- Zc:implicitNoexcept
- -Zc:implicitNoexcept
ms.assetid: 71807652-6f9d-436b-899e-f52daa6f500b
ms.openlocfilehash: bb1a632ffe684ac0777d0089a2edfd514bf66d0b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223801"
---
# <a name="zcimplicitnoexcept-implicit-exception-specifiers"></a>/Zc:implicitNoexcept (niejawne specyfikatory wyjątków)

Gdy jest określona opcja **/Zc: implicitNoexcept** , kompilator dodaje niejawny specyfikator wyjątku [noexcept](../../cpp/noexcept-cpp.md) do specjalnych funkcji składowych zdefiniowanych przez kompilator oraz do destruktorów zdefiniowanych przez użytkownika i dealokacji. Domyślnie **/Zc: implicitNoexcept** jest włączona, aby była zgodna ze standardem ISO c++ 11. Wyłączenie tej opcji wyłącza niejawnie **`noexcept`** w przypadku destruktorów zdefiniowanych przez użytkownika i dealloacators oraz specjalnych funkcji składowych zdefiniowanych przez kompilator.

## <a name="syntax"></a>Składnia

> **/Zc: implicitNoexcept**[ **-** ]

## <a name="remarks"></a>Uwagi

**/Zc: implicitNoexcept** instruuje kompilator, aby przestrzegał sekcji 15,4 standardu ISO c++ 11. Niejawnie dodaje **`noexcept`** specyfikator wyjątku do każdej niejawnie zadeklarowanej lub jawnie domyślnej specjalnej funkcji składowej — Konstruktor domyślny, Konstruktor kopiujący, Konstruktor przenoszenia, destruktor, operator przypisania kopiowania lub operator przypisania przenoszenia — oraz każdy destruktor zdefiniowany przez użytkownika lub funkcję dealokacji. Zdefiniowany przez użytkownika deprzypisanie ma niejawny `noexcept(true)` specyfikator wyjątku. Dla destruktorów zdefiniowanych przez użytkownika, niejawny specyfikator wyjątku jest `noexcept(true)` chyba, że w klasie składowej lub klasie bazowej nie ma destruktora, który nie jest `noexcept(true)` . W przypadku funkcji specjalnych elementów członkowskich generowanych przez kompilator, jeśli jakakolwiek funkcja wywoływana bezpośrednio przez tę funkcję jest skuteczna `noexcept(false)` , niejawny specyfikator wyjątku to `noexcept(false)` . W przeciwnym razie niejawny specyfikator wyjątku to `noexcept(true)` .

Kompilator nie generuje niejawnego specyfikatora wyjątku dla funkcji zadeklarowanych za pomocą jawnych **`noexcept`** lub **`throw`** specyfikatorów lub `__declspec(nothrow)` atrybutu.

Domyślnie **/Zc: implicitNoexcept** jest włączona. Opcja [/permissive-](permissive-standards-conformance.md) nie ma wpływu na **/Zc: implicitNoexcept**.

Jeśli opcja jest wyłączona przez określenie **/Zc: implicitNoexcept-**, w kompilatorze nie są generowane żadne niejawne specyfikatory wyjątków. Takie zachowanie jest takie samo jak Visual Studio 2013, gdzie destruktory i dekonstruktory, które nie mają specyfikatorów wyjątków, mogą mieć **`throw`** instrukcje. Domyślnie, a gdy **/Zc: implicitNoexcept** jest określony, jeśli **`throw`** instrukcja zostanie napotkana w czasie wykonywania w funkcji z specyfikatorem niejawnym `noexcept(true)` , powoduje natychmiastowe wywołanie `std::terminate` i normalne zachowanie odwinięcia dla programów obsługi wyjątków. Aby pomóc w zidentyfikowaniu tej sytuacji, kompilator generuje [Ostrzeżenie kompilatora (poziom 1) C4297](../../error-messages/compiler-warnings/compiler-warning-level-1-c4297.md). Jeśli **`throw`** jest zamierzone, zalecamy zmianę deklaracji funkcji tak, aby zawierała jawny `noexcept(false)` specyfikator zamiast używania **/Zc: implicitNoexcept-**.

Ten przykład pokazuje, jak zdefiniowany przez użytkownika destruktor, który nie ma jawnego specyfikatora wyjątku zachowuje się, gdy opcja **/Zc: implicitNoexcept** jest ustawiona lub wyłączona. Aby wyświetlić zachowanie po ustawieniu, Kompiluj przy użyciu `cl /EHsc /W4 implicitNoexcept.cpp` . Aby wyświetlić zachowanie po wyłączeniu, Kompiluj przy użyciu `cl /EHsc /W4 /Zc:implicitNoexcept- implicitNoexcept.cpp` .

```cpp
// implicitNoexcept.cpp
// Compile by using: cl /EHsc /W4 implicitNoexcept.cpp
// Compile by using: cl /EHsc /W4 /Zc:implicitNoexcept- implicitNoexcept.cpp

#include <iostream>
#include <cstdlib>      // for std::exit, EXIT_FAILURE, EXIT_SUCCESS
#include <exception>    // for std::set_terminate

void my_terminate()
{
    std::cout << "Unexpected throw caused std::terminate" << std::endl;
    std::cout << "Exit returning EXIT_FAILURE" << std::endl;
    std::exit(EXIT_FAILURE);
}

struct A {
    // Explicit noexcept overrides implicit exception specification
    ~A() noexcept(false) {
        throw 1;
    }
};

struct B : public A {
    // Compiler-generated ~B() definition inherits noexcept(false)
    ~B() = default;
};

struct C {
    // By default, the compiler generates an implicit noexcept(true)
    // specifier for this user-defined destructor. To enable it to
    // throw an exception, use an explicit noexcept(false) specifier,
    // or compile by using /Zc:implicitNoexcept-
    ~C() {
        throw 1; // C4297, calls std::terminate() at run time
    }
};

struct D : public C {
    // This destructor gets the implicit specifier of its base.
    ~D() = default;
};

int main()
{
    std::set_terminate(my_terminate);

    try
    {
        {
            B b;
        }
    }
    catch (...)
    {
        // exception should reach here in all cases
        std::cout << "~B Exception caught" << std::endl;
    }
    try
    {
        {
            D d;
        }
    }
    catch (...)
    {
        // exception should not reach here if /Zc:implicitNoexcept
        std::cout << "~D Exception caught" << std::endl;
    }
    std::cout << "Exit returning EXIT_SUCCESS" << std::endl;
    return EXIT_SUCCESS;
}
```

Podczas kompilowania przy użyciu domyślnego ustawienia **/Zc: implicitNoexcept**, przykład generuje te dane wyjściowe:

```Output
~B Exception caught
Unexpected throw caused std::terminate
Exit returning EXIT_FAILURE
```

Podczas kompilowania przy użyciu ustawienia **/Zc: implicitNoexcept-**, przykład generuje te dane wyjściowe:

```Output
~B Exception caught
~D Exception caught
Exit returning EXIT_SUCCESS
```

Aby uzyskać więcej informacji na temat problemów ze zgodnością w Visual C++, zobacz [niestandardowe zachowanie](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **Configuration Properties**  >  stronę właściwości konfiguracja wiersza polecenia**C/C++**  >  **Command Line** .

1. Zmodyfikuj właściwość **Opcje dodatkowe** , aby uwzględnić **/Zc: implicitNoexcept** lub **/Zc: implicitNoexcept-** , a następnie wybierz **przycisk OK**.

## <a name="see-also"></a>Zobacz także

[/Zc (Zgodność)](zc-conformance.md)<br/>
[noexcept](../../cpp/noexcept-cpp.md)<br/>
[Specyfikacje wyjątków (throw)](../../cpp/exception-specifications-throw-cpp.md)<br/>
[kończyć](../../standard-library/exception-functions.md#terminate)<br/>
