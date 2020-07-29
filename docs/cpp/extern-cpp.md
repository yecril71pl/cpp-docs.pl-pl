---
title: :::no-loc(extern):::Języków
description: 'Wskazówki dotyczące :::no-loc(extern)::: słowa kluczowego języka C++.'
ms.date: 01/28/2020
f1_keywords:
- ':::no-loc(extern):::'
- :::no-loc(extern):::_CPP
helpviewer_keywords:
- ':::no-loc(extern)::: keyword [C++], linkage to non-C++ functions'
- declarations, :::no-loc(extern):::al
- ':::no-loc(extern):::al linkage, :::no-loc(extern)::: modifier'
ms.assetid: 1e2f0ae3-ae98-4410-85b5-222d6abc865a
no-loc:
- ':::no-loc(extern):::'
- ':::no-loc(const):::'
- ':::no-loc(constexpr):::'
- ':::no-loc(permissive):::'
ms.openlocfilehash: 510352f9e99e513f4a426f6ef89be4474085d97c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227507"
---
# <a name="no-locextern-c"></a>:::no-loc(extern):::Języków

**`:::no-loc(extern):::`** Słowo kluczowe może być zastosowane do globalnej zmiennej, funkcji lub deklaracji szablonu. Określa, że symbol ma * :::no-loc(extern)::: połączenie Al*. Aby uzyskać ogólne informacje na temat powiązania i dlaczego nie zaleca się używania zmiennych globalnych, zobacz [jednostki translacji i powiązania](program-and-linkage-cpp.md).

**`:::no-loc(extern):::`** Słowo kluczowe ma cztery znaczenia w zależności od kontekstu:

- W **`:::no-loc(const):::`** deklaracji zmiennej nieglobalnej określa, **`:::no-loc(extern):::`** że zmienna lub funkcja jest zdefiniowana w innej jednostce tłumaczenia. **`:::no-loc(extern):::`** Należy zastosować wszystkie pliki z wyjątkiem tego, gdzie zmienna jest zdefiniowana.

- W **`:::no-loc(const):::`** deklaracji zmiennej określa, że zmienna ma :::no-loc(extern)::: połączenie Al. **`:::no-loc(extern):::`** Należy zastosować do wszystkich deklaracji we wszystkich plikach. ( **`:::no-loc(const):::`** Zmienne globalne mają domyślnie powiązania wewnętrzne).

- ** :::no-loc(extern)::: "C"** określa, że funkcja jest zdefiniowana w innym miejscu i używa konwencji wywoływania języka C. :::no-loc(extern):::Modyfikator "C" może być również stosowany do wielu deklaracji funkcji w bloku.

- W deklaracji szablonu określa, **`:::no-loc(extern):::`** że szablon został już skonkretyzowany w innym miejscu. **`:::no-loc(extern):::`** informuje kompilator, że może ponownie użyć innego wystąpienia, zamiast tworzyć nowe w bieżącej lokalizacji. Aby uzyskać więcej informacji na temat tego sposobu korzystania z programu **`:::no-loc(extern):::`** , zobacz [jawne Tworzenie wystąpienia](explicit-instantiation.md).

## <a name="no-locextern-linkage-for-non-no-locconst-globals"></a>:::no-loc(extern):::połączenie z :::no-loc(const)::: nieglobals

Gdy konsolidator widzi **`:::no-loc(extern):::`** przed deklaracją zmiennej globalnej, szuka definicji w innej jednostce tłumaczenia. Deklaracje innych niż **`:::no-loc(const):::`** zmienne w zakresie globalnym mają :::no-loc(extern)::: Domyślnie wartość Al. Dotyczy tylko **`:::no-loc(extern):::`** deklaracji, które nie zawierają definicji.

```cpp
//fileA.cpp
int i = 42; // declaration and definition

//fileB.cpp
:::no-loc(extern)::: int i;  // declaration only. same as i in FileA

//fileC.cpp
:::no-loc(extern)::: int i;  // declaration only. same as i in FileA

//fileD.cpp
int i = 43; // LNK2005! 'i' already has a definition.
:::no-loc(extern)::: int i = 43; // same error (:::no-loc(extern)::: is ignored on definitions)
```

## <a name="no-locextern-linkage-for-no-locconst-globals"></a>:::no-loc(extern):::połączenie z :::no-loc(const)::: Globals

**`:::no-loc(const):::`** Zmienna globalna ma domyślnie powiązania wewnętrzne. Jeśli chcesz, aby zmienna miała :::no-loc(extern)::: połączenie Al, Zastosuj **`:::no-loc(extern):::`** słowo kluczowe do definicji oraz wszystkie inne deklaracje w innych plikach:

```cpp
//fileA.cpp
:::no-loc(extern)::: :::no-loc(const)::: int i = 42; // :::no-loc(extern)::: :::no-loc(const)::: definition

//fileB.cpp
:::no-loc(extern)::: :::no-loc(const)::: int i;  // declaration only. same as i in FileA
```

## <a name="no-locextern-no-locconstexpr-linkage"></a>:::no-loc(extern)::::::no-loc(constexpr):::połączenie

W programie Visual Studio 2017 w wersji 15,3 lub starszej kompilator zawsze otrzymał **`:::no-loc(constexpr):::`** zmienną połączenie wewnętrzne, nawet gdy zmienna została oznaczona **`:::no-loc(extern):::`** . W programie Visual Studio 2017 w wersji 15,5 lub nowszej przełącznik kompilatora [/Zc: :::no-loc(extern)::: constexpr](../build/reference/zc-:::no-loc(extern)::::::no-loc(constexpr):::.md) włącza poprawne standardy — zgodność z zachowaniem. Ostatecznie opcja stanie się wartością domyślną. [/:::no-loc(permissive):::-](../build/reference/:::no-loc(permissive):::-standards-conformance.md)Opcja nie włącza **/Zc: :::no-loc(extern)::: constexpr**.

```cpp
:::no-loc(extern)::: :::no-loc(constexpr)::: int x = 10; //error LNK2005: "int :::no-loc(const)::: x" already defined
```

Jeśli plik nagłówkowy zawiera zmienną zadeklarowaną **`:::no-loc(extern):::`** **`:::no-loc(constexpr):::`** , musi być oznaczona jako `__declspec(selectany)` prawidłowo, aby zawierała zduplikowane deklaracje:

```cpp
:::no-loc(extern)::: :::no-loc(constexpr)::: __declspec(selectany) int x = 10;
```

## <a name="no-locextern-c-and-no-locextern-c-function-declarations"></a>:::no-loc(extern):::Deklaracje funkcji "C" i :::no-loc(extern)::: "C++"

W języku C++, gdy jest używany z ciągiem, **`:::no-loc(extern):::`** określa, że stosowane są konwencje łączenia innego języka dla deklarator. Funkcje i dane języka c są dostępne tylko wtedy, gdy są one wcześniej zadeklarowane jako posiadające powiązanie C. Jednak muszą być zdefiniowane w oddzielnie skompilowanej jednostce translacji.

Język Microsoft C++ obsługuje ciągi **"C"** i **"C++"** w polu *literał ciągu* . Wszystkie standardowe pliki dyrektywy include używają składni ** :::no-loc(extern)::: "C"** , aby zezwalać na używanie funkcji biblioteki wykonawczej w programach C++.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak zadeklarować nazwy, które mają połączenie C:

```cpp
// Declare printf with C linkage.
:::no-loc(extern)::: "C" int printf(:::no-loc(const)::: char *fmt, ...);

//  Cause everything in the specified
//  header files to have C linkage.
:::no-loc(extern)::: "C" {
    // add your #include statements here
#include <stdio.h>
}

//  Declare the two functions ShowChar
//  and GetChar with C linkage.
:::no-loc(extern)::: "C" {
    char ShowChar(char ch);
    char GetChar(void);
}

//  Define the two functions
//  ShowChar and GetChar with C linkage.
:::no-loc(extern)::: "C" char ShowChar(char ch) {
    putchar(ch);
    return ch;
}

:::no-loc(extern)::: "C" char GetChar(void) {
    char ch;
    ch = getchar();
    return ch;
}

// Declare a global variable, errno, with C linkage.
:::no-loc(extern)::: "C" int errno;
```

Jeśli funkcja ma więcej niż jedną specyfikację powiązania, muszą one wyrazić zgodę. Wystąpił błąd podczas deklarowania funkcji jako powiązania C i C++. Ponadto, jeśli dwie deklaracje dla funkcji występują w programie — jedna ze specyfikacją powiązania i jedna bez niej — deklaracja ze specyfikacją powiązania musi być pierwsza. Wszystkim nadmiarowym deklaracjom funkcji, które mają już specyfikację, nadawane są specyfikacje powiązania określone w pierwszej deklaracji. Na przykład:

```cpp
:::no-loc(extern)::: "C" int CFunc1();
...
int CFunc1();            // Redeclaration is benign; C linkage is
                         //  retained.

int CFunc2();
...
:::no-loc(extern)::: "C" int CFunc2(); // Error: not the first declaration of
                         //  CFunc2;  cannot contain linkage
                         //  specifier.
```

## <a name="see-also"></a>Zobacz także

[Służąc](../cpp/keywords-cpp.md)\
[Jednostki tłumaczenia i powiązania](program-and-linkage-cpp.md)\
[:::no-loc(extern):::Specyfikator klasy magazynu w języku C](../c-language/:::no-loc(extern):::-storage-class-specifier.md)\
[Zachowanie identyfikatorów w języku C](../c-language/behavior-of-identifiers.md)\
[Połączenie w języku C](../c-language/linkage.md)
