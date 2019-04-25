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
ms.openlocfilehash: ec2b8c8fb4c7730a78c4403606d6fa61c0ddc374
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315563"
---
# <a name="zcimplicitnoexcept-implicit-exception-specifiers"></a>/Zc:implicitNoexcept (niejawne specyfikatory wyjątków)

Gdy **/Zc: implicitnoexcept** opcja zostanie określona, kompilator dodający ukrytego [noexcept](../../cpp/noexcept-cpp.md) specyfikator wyjątku do zdefiniowanego przez kompilator specjalnych funkcji Członkowskich i zdefiniowanych przez użytkownika destruktorów i deallocators. Domyślnie **/Zc: implicitnoexcept** jest włączona, aby były zgodne z normą ISO C ++ 11, standard. Włączenie tej opcji wyłącza niejawne `noexcept` na zdefiniowanych przez użytkownika destruktorów i dealloacators i zdefiniowanego przez kompilator specjalnych funkcji Członkowskich.

## <a name="syntax"></a>Składnia

> **/Zc:implicitNoexcept**[**-**]

## <a name="remarks"></a>Uwagi

**/ Zc: implicitnoexcept** informuje kompilator, postępuj zgodnie z sekcją 15.4 ISO C ++ 11, standardowy. Niejawnie dodaje `noexcept` specyfikator wyjątek, aby każdy jawnie ustawione jako domyślne lub niejawnie deklarowana specjalna funkcja członkowska — Konstruktor domyślny, Kopiuj konstruktora, Konstruktor przenoszący, destruktor, operator przypisania kopiowania lub przenoszenia przypisania operator — i każdej funkcji zdefiniowanej przez użytkownika — destruktor lub program wycofujący przydzielenia. Program wycofujący przydzielenia zdefiniowanych przez użytkownika mają niejawny `noexcept(true)` specyfikator wyjątku. Zdefiniowane przez użytkownika destruktorów, specyfikator niejawne wyjątek jest `noexcept(true)` chyba że zamkniętego elementu członkowskiego klasy lub klasa bazowa ma destruktor, który nie jest `noexcept(true)`. Dla generowanych przez kompilator specjalnych funkcji Członkowskich, jeśli żadnej funkcji bezpośrednio wywoływane przez tę funkcję jest faktycznie `noexcept(false)`, specyfikator niejawne wyjątek jest `noexcept(false)`. W przeciwnym razie jest specyfikator niejawne wyjątek `noexcept(true)`.

Kompilator nie generuje specyfikatorem wyjątek niejawne funkcje zadeklarowane za pomocą jawnego `noexcept` lub `throw` specyfikatory lub `__declspec(nothrow)` atrybutu.

Domyślnie **/Zc: implicitnoexcept** jest włączona. [/ Permissive-](permissive-standards-conformance.md) opcji nie ma wpływu na **/Zc: implicitnoexcept**.

Jeśli ta opcja jest wyłączona, określając **/Zc:implicitNoexcept-**, nie specyfikatory wyjątków niejawne są generowane przez kompilator. To zachowanie jest taka sama jak Visual Studio 2013, gdzie może mieć destruktory i deallocators, które nie miały specyfikatory wyjątków `throw` instrukcji. Domyślnie i kiedy **/Zc: implicitnoexcept** jest określona, jeśli `throw` instrukcji zostanie osiągnięty w czasie wykonywania w funkcji za pomocą ukrytego `noexcept(true)` specyfikator powoduje natychmiastowe wywołanie `std::terminate`, i normalne zachowanie odwijania dla obsługi wyjątków nie jest gwarantowana. Aby ułatwić identyfikację tę sytuację, kompilator generuje [ostrzeżenie kompilatora (poziom 1) C4297](../../error-messages/compiler-warnings/compiler-warning-level-1-c4297.md). Jeśli `throw` jest zamierzone, zaleca się zmienić swoje deklaracji funkcji, aby jawnie `noexcept(false)` specyfikator zamiast **/Zc:implicitNoexcept-**.

W tym przykładzie pokazano, jak destruktor zdefiniowany przez użytkownika, zawierającej specyfikator nie jawnych wyjątków zachowuje się kiedy **/Zc: implicitnoexcept** opcji jest ustawiona lub wyłączone. Aby wyświetlić zachowanie po ustawieniu kompilowania przy użyciu `cl /EHsc /W4 implicitNoexcept.cpp`. Aby wyświetlić zachowanie wyłączenia, kompilowania przy użyciu `cl /EHsc /W4 /Zc:implicitNoexcept- implicitNoexcept.cpp`.

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

Gdy kompilowany przy użyciu domyślnego ustawienia **/Zc: implicitnoexcept**, przykład generuje następujące dane wyjściowe:

```Output
~B Exception caught
Unexpected throw caused std::terminate
Exit returning EXIT_FAILURE
```

Podczas kompilowania przy użyciu ustawienia **/Zc:implicitNoexcept-**, przykład generuje następujące dane wyjściowe:

```Output
~B Exception caught
~D Exception caught
Exit returning EXIT_SUCCESS
```

Aby uzyskać więcej informacji na temat problemów ze zgodnością w języku Visual C++, zobacz [niestandardowe zachowanie](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **wiersza polecenia** stronę właściwości.

1. Modyfikowanie **dodatkowe opcje** właściwości do uwzględnienia **/Zc: implicitnoexcept** lub **/Zc:implicitNoexcept-** , a następnie wybierz **OK**.

## <a name="see-also"></a>Zobacz także

[/Zc (Zgodność)](zc-conformance.md)<br/>
[noexcept](../../cpp/noexcept-cpp.md)<br/>
[Specyfikacje wyjątków (throw)](../../cpp/exception-specifications-throw-cpp.md)<br/>
[Zakończenie](../../standard-library/exception-functions.md#terminate)<br/>
