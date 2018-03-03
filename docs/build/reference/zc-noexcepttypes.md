---
title: "-Zc-: noexceptTypes (C ++ 17 noexcept reguły) | Dokumentacja firmy Microsoft"
ms.date: 11/14/2017
ms.technology:
- cpp-tools
ms.topic: article
f1_keywords:
- /Zc:noexceptTypes
dev_langs:
- C++
helpviewer_keywords:
- /Zc:noexceptTypes
- Zc:noexceptTypes
- -Zc:noexceptTypes
ms.assetid: 1cbf7e3c-0f82-4f91-84dd-612bcf26d2c6
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e1b0e209462295f907f5e518299d34fb18aade4d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="zcnoexcepttypes-c17-noexcept-rules"></a>/Zc:noexceptTypes (c ++ 17 noexcept zasad)

Sprawia, że standardzie C ++ 17 `throw()` jako alias `noexcept`, usuwa `throw(<type list>)` i `throw(...)`i umożliwia pewnych typów uwzględnić `noexcept`. Może to spowodować szereg problemów ze zgodnością źródła w kodzie, który odpowiada C ++ 14 lub wcześniej. **/Zc:noexceptTypes** opcji można określić zgodność na standardzie C ++ 17 lub zezwolić C ++ 14 i starsze wersje zachowania podczas kompilowania kodu w trybie C ++ 17.

## <a name="syntax"></a>Składnia

> **/Zc:noexceptTypes**[-]

## <a name="remarks"></a>Uwagi

Gdy **/Zc:noexceptTypes** zostanie określona opcja, kompilator odpowiada w standardzie C ++ 17 i traktuje [throw()](../../cpp/exception-specifications-throw-cpp.md) jako alias [noexcept](../../cpp/noexcept-cpp.md), usuwa `throw(<type list>)`i `throw(...)`i umożliwia pewnych typów uwzględnić `noexcept`. **/Zc:noexceptTypes** opcja jest dostępna tylko podczas [/std:c ++ 17](std-specify-language-standard-version.md) lub [/std:latest](std-specify-language-standard-version.md) jest włączona. **/Zc:noexceptTypes** jest domyślnie włączone są zgodne z normą ISO w standardzie C ++ 17. Wyłącz tę opcję, określając **/Zc:noexceptTypes-** powraca do języka C ++ 14 zachowanie `noexcept` podczas **/std::C ++ 17** lub **/std::latest** jest określona.

Począwszy od programu Visual Studio 2017 15,5 cala wersji kompilatora języka C++ diagnozuje więcej specyfikacje wyjątków niedopasowanych w deklaracjach trybu C ++ 17 lub gdy [/ ograniczająca-](permissive-standards-conformance.md) określono opcję.

W tym przykładzie pokazano deklaracje ze specyfikatorem wyjątek zachowania podczas **/Zc:noexceptTypes** opcja jest ustawiona lub wyłączona. Aby wyświetlić zachowanie po ustawieniu skompilować przy użyciu `cl /EHsc /W4 noexceptTypes.cpp`. Aby wyświetlić zachowanie wyłączenia, skompilować przy użyciu `cl /EHsc /W4 /Zc:noexceptTypes- noexceptTypes.cpp`.

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

Podczas kompilacji za pomocą ustawienia domyślne **/Zc:noexceptTypes**, próbki generuje wymienionych ostrzeżenia. Aby zaktualizować kodu, użyj następujących czynności:

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

Aby uzyskać więcej informacji na temat problemów zgodności w programie Visual C++, zobacz [niestandardowe zachowanie](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **wiersza polecenia** stronę właściwości w **C/C++** folderu.

1. Modyfikowanie **dodatkowe opcje** właściwości, aby uwzględnić **/Zc:noexceptTypes** lub **/Zc:noexceptTypes-** , a następnie wybierz **OK**.

## <a name="see-also"></a>Zobacz także

[/Zc (Zgodność)](../../build/reference/zc-conformance.md)  
[noexcept](../../cpp/noexcept-cpp.md)  
[Specyfikacje wyjątków (throw)](../../cpp/exception-specifications-throw-cpp.md)  
