---
title: /Zc:noexceptTypes (reguły języka c ++ 17 noexcept)
ms.date: 11/14/2017
f1_keywords:
- /Zc:noexceptTypes
helpviewer_keywords:
- /Zc:noexceptTypes
- Zc:noexceptTypes
- -Zc:noexceptTypes
ms.assetid: 1cbf7e3c-0f82-4f91-84dd-612bcf26d2c6
ms.openlocfilehash: 28e06f54049d36262134b6be7eadb0e6e5349a45
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57812112"
---
# <a name="zcnoexcepttypes-c17-noexcept-rules"></a>/Zc:noexceptTypes (reguły języka c ++ 17 noexcept)

Sprawia, że standardzie C ++ 17 `throw()` jako alias `noexcept`, usuwa `throw(<type list>)` i `throw(...)`i umożliwia pewnych typów uwzględnić `noexcept`. Może to spowodować szereg problemów ze zgodnością źródła w kodzie, który jest zgodny, C ++ 14 lub wcześniej. **/Zc:noexceptTypes** opcji można określić zgodność na standardzie C ++ 17 lub zezwalać na C ++ 14 i starsze zachowanie, gdy kod jest kompilowany w trybie C ++ 17.

## <a name="syntax"></a>Składnia

> **/Zc:noexceptTypes**[-]

## <a name="remarks"></a>Uwagi

Gdy **/Zc:noexceptTypes** opcja zostanie określona, kompilator odpowiada w standardzie C ++ 17 i traktuje [throw()](../../cpp/exception-specifications-throw-cpp.md) jako alias [noexcept](../../cpp/noexcept-cpp.md), usuwa `throw(<type list>)`i `throw(...)`i umożliwia pewnych typów uwzględnić `noexcept`. **/Zc:noexceptTypes** opcja jest dostępna tylko podczas [/STD: c ++ 17](std-specify-language-standard-version.md) lub [/std:latest](std-specify-language-standard-version.md) jest włączona. **/Zc:noexceptTypes** jest domyślnie włączona, aby były zgodne z normą ISO w standardzie C ++ 17. [/ Permissive-](permissive-standards-conformance.md) opcji nie ma wpływu na **/Zc:noexceptTypes**. Wyłącz tę opcję, określając **/Zc:noexceptTypes-** powraca do języka C ++ 14 zachowanie `noexcept` podczas **/std::C ++ 17** lub **/std::latest** jest określony.

Począwszy od programu Visual Studio 2017 w wersji 15.5, kompilator języka C++ diagnozuje więcej specyfikacje wyjątków niezgodne w deklaracjach trybem C ++ 17 lub [/ permissive-](permissive-standards-conformance.md) określono opcję.

W tym przykładzie pokazano deklaracje ze specyfikatorem wyjątków zachowanie kiedy **/Zc:noexceptTypes** opcji jest ustawiona lub wyłączone. Aby wyświetlić zachowanie po ustawieniu kompilowania przy użyciu `cl /EHsc /W4 noexceptTypes.cpp`. Aby wyświetlić zachowanie wyłączenia, kompilowania przy użyciu `cl /EHsc /W4 /Zc:noexceptTypes- noexceptTypes.cpp`.

```cpp
// noexceptTypes.cpp
// Compile by using: cl /EHsc /W4 noexceptTypes.cpp
// Compile by using: cl /EHsc /W4 /Zc:noexceptTypes- noexceptTypes.cpp

void f() throw();    // equivalent to void f() noexcept;
void f() { }         // warning C5043
void g() throw(...); // warning C5040

struct A
{
    virtual void f() throw();
};

struct B : A
{
    virtual void f() { } // error C2694
};
```

Gdy kompilowany przy użyciu domyślnego ustawienia **/Zc:noexceptTypes**, przykład generuje ostrzeżenia uwzględnione na liście. Aby zaktualizować swój kod, użyj następującego polecenia zamiast tego:

```cpp
void f() noexcept;
void f() noexcept { }
void g() noexcept(false);

struct A
{
    virtual void f() noexcept;
};

struct B : A
{
    virtual void f() noexcept { }
};
```

Aby uzyskać więcej informacji na temat problemów ze zgodnością w języku Visual C++, zobacz [niestandardowe zachowanie](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **wiersza polecenia** stronę właściwości.

1. Modyfikowanie **dodatkowe opcje** właściwości do uwzględnienia **/Zc:noexceptTypes** lub **/Zc:noexceptTypes-** , a następnie wybierz **OK**.

## <a name="see-also"></a>Zobacz także

[/Zc (Zgodność)](zc-conformance.md)<br/>
[noexcept](../../cpp/noexcept-cpp.md)<br/>
[Specyfikacje wyjątków (throw)](../../cpp/exception-specifications-throw-cpp.md)
