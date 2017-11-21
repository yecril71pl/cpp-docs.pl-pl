---
title: "-Zc: implicitNoexcept (niejawne specyfikatory wyjątków) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /Zc:implicitNoexcept
dev_langs: C++
helpviewer_keywords:
- /Zc:implicitNoexcept
- Zc:implicitNoexcept
- -Zc:implicitNoexcept
ms.assetid: 71807652-6f9d-436b-899e-f52daa6f500b
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 20789d226ace8ba41a9635f0039274b68d37922c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="zcimplicitnoexcept-implicit-exception-specifiers"></a>/Zc:implicitNoexcept (niejawne specyfikatory wyjątków)
Gdy **/Zc: implicitnoexcept** zostanie określona opcja, kompilator dodaje niejawny [noexcept](../../cpp/noexcept-cpp.md) specyfikator wyjątków zdefiniowanych przez kompilator specjalnych funkcji Członkowskich i destruktory zdefiniowane przez użytkownika i deallocators. Domyślnie **/Zc: implicitnoexcept** jest włączona, aby był zgodny ze standardem C ++ 11 ISO. Włączenie tej opcji wyłącza niejawne `noexcept` destruktory zdefiniowane przez użytkownika i dealloacators i zdefiniowanych przez kompilator specjalnych funkcji Członkowskich.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
/Zc:implicitNoexcept[-]  
```  
  
#### <a name="parameters"></a>Parametry  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie, a jeśli **/Zc: implicitnoexcept** jest określony, kompilator następuje sekcji 15.4 ISO standardem C ++ 11 i dodaje niejawnie `noexcept` specyfikator wyjątek do każdego zadeklarowanym niejawnie lub jawnie ustawiana domyślnie specjalnej funkcji członkowskiej — Konstruktor domyślny Konstruktor kopiujący, Konstruktor przenoszenia, destruktor, operatora przypisania kopii lub operator przypisania przenoszenia — i każdego użytkownika — destruktor lub program wycofujący przydzielenia funkcji. Program wycofujący przydzielenia użytkownika ma niejawne `noexcept(true)` specyfikator wyjątku. Dla użytkownika destruktory specyfikator niejawne wyjątku jest `noexcept(true)` chyba że zamkniętego elementu członkowskiego klasy lub klasa bazowa ma destruktor, który nie jest `noexcept(true)`. Dla generowane przez kompilator specjalnych funkcji Członkowskich, jeśli dowolne funkcje wywoływane bezpośrednio przez tę funkcję jest skutecznie `noexcept(false)`, specyfikator niejawne wyjątku jest `noexcept(false)`. W przeciwnym razie specyfikator niejawne wyjątku jest `noexcept(true)`.  
  
 Kompilator nie generuje specyfikator niejawne wyjątku dla funkcji zadeklarowany za pomocą jawnego `noexcept` lub `throw` specyfikatory lub `__declspec(nothrow)` atrybutu.  
  
 Jeśli opcja jest wyłączona, określając **/Zc:implicitNoexcept-**, nie specyfikatory wyjątków niejawne są generowane przez kompilator. To zachowanie jest taka sama jak Visual Studio 2013, gdzie mają destruktory i deallocators, które nie ma specyfikatory wyjątków `throw` instrukcje. Domyślnie, gdy **/Zc: implicitnoexcept** jest określony, jeśli `throw` napotkano instrukcji w czasie wykonywania w funkcji z niejawny `noexcept(true)` specyfikator, powoduje natychmiastowe wywołanie `std::terminate`, i normalne zachowanie odwijaniem dla programów obsługi wyjątków nie jest gwarantowana. Aby ułatwić identyfikację tej sytuacji, kompilator generuje [C4297 ostrzeżenie kompilatora (poziom 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4297.md). Jeśli `throw` jest zamierzone, zaleca się zmiany z deklaracją funkcji mieć jawną `noexcept(false)` specyfikator zamiast **/Zc:implicitNoexcept-**.  
  
 W tym przykładzie pokazano, jak destruktora zdefiniowane przez użytkownika mającego nie specyfikator jawne wyjątek ma zachowywać się podczas **/Zc: implicitnoexcept** opcja jest ustawiona lub wyłączona. Aby wyświetlić zachowanie po ustawieniu skompilować przy użyciu `cl /EHsc /W4 implicitNoexcept.cpp`. Aby wyświetlić zachowanie wyłączenia, skompilować przy użyciu `cl /EHsc /W4 /Zc:implicitNoexcept- implicitNoexcept.cpp`.  
  
```  
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
  
 Podczas kompilacji za pomocą ustawienia domyślne **/Zc: implicitnoexcept**, próbki generuje te dane wyjściowe:  
  
```Output  
~B Exception caught  
Unexpected throw caused std::terminate  
Exit returning EXIT_FAILURE  
```  
  
 Podczas kompilacji za pomocą ustawienia **/Zc:implicitNoexcept-**, próbki generuje te dane wyjściowe:  
  
```Output  
~B Exception caught  
~D Exception caught  
Exit returning EXIT_SUCCESS  
```  
  
 Aby uzyskać więcej informacji na temat problemów zgodności w programie Visual C++, zobacz [niestandardowe zachowanie](../../cpp/nonstandard-behavior.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Wybierz **C/C++** folderu.  
  
3.  Wybierz **wiersza polecenia** strony właściwości.  
  
4.  Modyfikowanie **dodatkowe opcje** właściwości, aby uwzględnić **/Zc: implicitnoexcept** lub **/Zc:implicitNoexcept-** , a następnie wybierz **OK**.  
  
## <a name="see-also"></a>Zobacz też  
 [/Zc (zgodność)](../../build/reference/zc-conformance.md)   
 [noexcept](../../cpp/noexcept-cpp.md)   
 [Specyfikacje wyjątków (throw)](../../cpp/exception-specifications-throw-cpp.md)   
 [Zakończenie](../../standard-library/exception-functions.md#terminate)