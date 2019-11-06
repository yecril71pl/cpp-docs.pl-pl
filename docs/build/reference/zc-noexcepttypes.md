---
title: /Zc:noexceptTypes (Zasady C++17 noexcept)
ms.date: 11/14/2017
f1_keywords:
- /Zc:noexceptTypes
helpviewer_keywords:
- /Zc:noexceptTypes
- Zc:noexceptTypes
- -Zc:noexceptTypes
ms.assetid: 1cbf7e3c-0f82-4f91-84dd-612bcf26d2c6
ms.openlocfilehash: 35bea7c2c629c615c60a6136f289b6b11926c054
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2019
ms.locfileid: "73624864"
---
# <a name="zcnoexcepttypes-c17-noexcept-rules"></a>/Zc:noexceptTypes (Zasady C++17 noexcept)

Standard C++ 17 sprawia, `throw()` alias `noexcept`, usuwa `throw(<type list>)` i `throw(...)`i zezwala na niektóre typy do dołączenia `noexcept`. Ta zmiana może powodować występowanie wielu problemów ze zgodnością źródła w kodzie, który jest zgodny z językiem C++ 14 lub wcześniejszym. Opcja **/Zc: noexceptTypes** określa zgodność ze standardem c++ 17. **/Zc: noexceptTypes —** umożliwia zachowanie języka c++ 14 i jego wcześniejszych wersji, gdy kod jest kompilowany w trybie c++ 17.

## <a name="syntax"></a>Składnia

> **/Zc: noexceptTypes**[-]

## <a name="remarks"></a>Uwagi

Gdy określona jest opcja **/Zc: noexceptTypes** , kompilator jest zgodny ze standardem c++ 17 i traktuje [throw ()](../../cpp/exception-specifications-throw-cpp.md) jako alias dla [noexcept](../../cpp/noexcept-cpp.md), usuwa `throw(<type list>)` i `throw(...)`i zezwala na niektóre typy do dołączenia `noexcept`. Opcja **/Zc: noexceptTypes** jest dostępna tylko wtedy, gdy jest włączona funkcja [/std: c++ 17](std-specify-language-standard-version.md) lub [/std: Najnowsza](std-specify-language-standard-version.md) . **/Zc: noexceptTypes** jest domyślnie włączona, aby była zgodna ze standardem ISO c++ 17. Opcja [/permissive-](permissive-standards-conformance.md) nie ma wpływu na **/Zc: noexceptTypes**. Wyłącz tę opcję, określając **/Zc: noexceptTypes-** , aby powrócić do zachowania języka c++ 14 `noexcept`, gdy zostanie określony **/std: c++ 17** lub **/std: Najnowsza** .

Począwszy od programu Visual Studio 2017 w wersji 15,5 C++ , kompilator diagnozuje bardziej niezgodne specyfikacje wyjątków w deklaracjach w trybie c++ 17 lub w przypadku określenia opcji [/permissive-](permissive-standards-conformance.md) .

Ten przykład pokazuje, jak deklaracje ze specyfikatorem wyjątku działają, gdy opcja **/Zc: noexceptTypes** jest ustawiona lub wyłączona. Aby wyświetlić zachowanie po ustawieniu, Kompiluj przy użyciu `cl /EHsc /W4 noexceptTypes.cpp`. Aby wyświetlić zachowanie po wyłączeniu, Kompiluj przy użyciu `cl /EHsc /W4 /Zc:noexceptTypes- noexceptTypes.cpp`.

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

Podczas kompilowania przy użyciu domyślnego ustawienia **/Zc: noexceptTypes**, przykład generuje wyświetlone ostrzeżenia. Aby zaktualizować kod, użyj następującego polecenia:

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

Aby uzyskać więcej informacji na temat problemów ze zgodnością C++w wizualizacji, zobacz [niestandardowe zachowanie](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [ C++ Ustawianie właściwości kompilatora i Build w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **Właściwości konfiguracji** > strony właściwości **wiersza polecenia** **C++ C/**  > .

1. Zmodyfikuj właściwość **Opcje dodatkowe** , aby uwzględnić **/Zc: noexceptTypes** lub **/Zc: noexceptTypes-** , a następnie wybierz **przycisk OK**.

## <a name="see-also"></a>Zobacz także

[/Zc (zgodność)](zc-conformance.md)\
[noexcept](../../cpp/noexcept-cpp.md)\
[Specyfikacje wyjątków (throw)](../../cpp/exception-specifications-throw-cpp.md)
