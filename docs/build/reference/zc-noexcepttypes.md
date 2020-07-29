---
title: /Zc:noexceptTypes (Zasady C++17 noexcept)
ms.date: 06/04/2020
f1_keywords:
- /Zc:noexceptTypes
helpviewer_keywords:
- /Zc:noexceptTypes
- Zc:noexceptTypes
- -Zc:noexceptTypes
ms.assetid: 1cbf7e3c-0f82-4f91-84dd-612bcf26d2c6
ms.openlocfilehash: 09817372e818a05c389a083aac5f04e03b1ab0e1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218952"
---
# <a name="zcnoexcepttypes-c17-noexcept-rules"></a>/Zc:noexceptTypes (Zasady C++17 noexcept)

Standard c++ 17 tworzy `throw()` alias dla **`noexcept`** , usuwa `throw(` *`type-list`* `)` i `throw(...)` i zezwala na uwzględnienie określonych typów **`noexcept`** . Ta zmiana może powodować występowanie wielu problemów ze zgodnością źródła w kodzie, który jest zgodny z językiem C++ 14 lub wcześniejszym. **`/Zc:noexceptTypes`** Opcja określa zgodność ze standardem c++ 17. **`/Zc:noexceptTypes-`** zezwala na zachowanie języka C++ 14 i jego wcześniejszych wersji, gdy kod jest kompilowany w trybie C++ 17.

## <a name="syntax"></a>Składnia

> **`/Zc:noexceptTypes`**\[**`-`**]

## <a name="remarks"></a>Uwagi

Gdy ta **`/Zc:noexceptTypes`** opcja jest określona, kompilator jest zgodny ze standardem c++ 17 i traktuje [**`throw()`**](../../cpp/exception-specifications-throw-cpp.md) jako alias dla [**`noexcept`**](../../cpp/noexcept-cpp.md) , usuwa `throw(` *`type-list`* `)` i `throw(...)` i zezwala na uwzględnienie określonych typów **`noexcept`** . Ta **`/Zc:noexceptTypes`** opcja jest dostępna tylko wtedy [**`/std:c++17`**](std-specify-language-standard-version.md) , gdy lub [**`/std:c++latest`**](std-specify-language-standard-version.md) jest włączona. **`/Zc:noexceptTypes`** jest domyślnie włączona, aby była zgodna ze standardem ISO C++ 17. Ta [**`/permissive-`**](permissive-standards-conformance.md) opcja nie ma wpływu **`/Zc:noexceptTypes`** . Wyłącz tę opcję, określając **`/Zc:noexceptTypes-`** , aby przywrócić zachowanie języka c++ 14, **`noexcept`** gdy **`/std:c++17`** lub **`/std:c++latest`** jest określony.

Począwszy od programu Visual Studio 2017 w wersji 15,5, kompilator języka C++ diagnozuje bardziej niezgodne specyfikacje wyjątków w deklaracjach w trybie C++ 17 lub po określeniu [**`/permissive-`**](permissive-standards-conformance.md) opcji.

Ten przykład pokazuje, jak deklaracje ze specyfikatorem wyjątku zachowują **`/Zc:noexceptTypes`** się, gdy opcja jest ustawiona lub wyłączona. Aby wyświetlić zachowanie po ustawieniu, Kompiluj przy użyciu `cl /EHsc /W4 noexceptTypes.cpp` . Aby wyświetlić zachowanie po wyłączeniu, Kompiluj przy użyciu `cl /EHsc /W4 /Zc:noexceptTypes- noexceptTypes.cpp` .

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

Po skompilowaniu przy użyciu domyślnego ustawienia **`/Zc:noexceptTypes`** , przykład generuje wyświetlone ostrzeżenia. Aby zaktualizować kod, użyj następującego polecenia:

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

Aby uzyskać więcej informacji na temat problemów ze zgodnością w Visual C++, zobacz [niestandardowe zachowanie](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **Configuration Properties**  >  stronę właściwości konfiguracja wiersza polecenia**C/C++**  >  **Command Line** .

1. Zmodyfikuj właściwość **Opcje dodatkowe** , aby uwzględnić *`/Zc:noexceptTypes`* lub *`/Zc:noexceptTypes-`* , a następnie wybierz przycisk **OK**.

## <a name="see-also"></a>Zobacz także

[**`/Zc`** Zgodności](zc-conformance.md)\
[noexcept](../../cpp/noexcept-cpp.md)\
[Specyfikacje wyjątków (throw)](../../cpp/exception-specifications-throw-cpp.md)
