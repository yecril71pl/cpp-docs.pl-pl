---
title: extern (C++)
description: Wskazówki dotyczące słowa C++ kluczowego extern języka.
ms.date: 01/28/2020
f1_keywords:
- extern
- extern_CPP
helpviewer_keywords:
- extern keyword [C++], linkage to non-C++ functions
- declarations, external
- external linkage, extern modifier
ms.assetid: 1e2f0ae3-ae98-4410-85b5-222d6abc865a
no-loc:
- extern
- const
- constexpr
- permissive
ms.openlocfilehash: 422b6960802c59f1c45e0c22a4a85988c808a5b3
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821769"
---
# <a name="opno-locextern-c"></a>extern (C++)

Słowo kluczowe **extern** może być stosowane do globalnej zmiennej, funkcji lub deklaracji szablonu. Określa, że symbol ma *powiązania zewnętrzne*. Aby uzyskać ogólne informacje na temat powiązania i dlaczego nie zaleca się używania zmiennych globalnych, zobacz [jednostki translacji i powiązania](program-and-linkage-cpp.md).

Słowo kluczowe **extern** ma cztery znaczenia w zależności od kontekstu:

- W deklaracji zmiennej globalnej innej niż **const** **extern** określa, że zmienna lub funkcja jest zdefiniowana w innej jednostce translacji. **extern** należy zastosować we wszystkich plikach, z wyjątkiem tego, gdzie zmienna jest zdefiniowana.

- W deklaracji zmiennej **const** określa, że zmienna ma powiązania zewnętrzne. **extern** należy zastosować do wszystkich deklaracji we wszystkich plikach. (Globalne zmienne **const** są domyślnie połączone wewnętrznie).

- **extern "C"** określa, że funkcja jest zdefiniowana w innym miejscu i używa konwencji wywoływania języka C. Modyfikator extern "C" może być również stosowany do wielu deklaracji funkcji w bloku.

- W deklaracji szablonu **extern** określa, że szablon został już skonkretyzowany w innym miejscu. **extern** informuje kompilator, że może ponownie użyć innego wystąpienia, zamiast tworzyć nowe w bieżącej lokalizacji. Aby uzyskać więcej informacji na temat korzystania z **extern** , zobacz [jawne Tworzenie wystąpienia](explicit-instantiation.md).

## <a name="opno-locextern-linkage-for-non-opno-locconst-globals"></a>extern połączenie z nieconstm Globals

Gdy konsolidator widzi **extern** przed deklaracją zmiennej globalnej, szuka definicji w innej jednostce tłumaczenia. Deklaracje zmiennych innych niż **const** w zakresie globalnym są domyślnie zewnętrzne. Zastosuj tylko **extern** do deklaracji, które nie zawierają definicji.

```cpp
//fileA.cpp
int i = 42; // declaration and definition

//fileB.cpp
extern int i;  // declaration only. same as i in FileA

//fileC.cpp
extern int i;  // declaration only. same as i in FileA

//fileD.cpp
int i = 43; // LNK2005! 'i' already has a definition.
extern int i = 43; // same error (extern is ignored on definitions)
```

## <a name="opno-locextern-linkage-for-opno-locconst-globals"></a>extern połączenie const Globals

Zmienna globalna **const** ma domyślnie powiązania wewnętrzne. Jeśli chcesz, aby zmienna miała połączenie zewnętrzne, Zastosuj słowo kluczowe **extern** do definicji oraz wszystkie inne deklaracje w innych plikach:

```cpp
//fileA.cpp
extern const int i = 42; // extern const definition

//fileB.cpp
extern const int i;  // declaration only. same as i in FileA
```

## <a name="opno-locextern-opno-locconstexpr-linkage"></a>połączenie constexpr extern

W programie Visual Studio 2017 w wersji 15,3 lub starszej kompilator zawsze udzielił **constexpr** zmiennej wewnętrznej powiązania, nawet gdy zmienna została oznaczona **extern** . W programie Visual Studio 2017 w wersji 15,5 lub nowszej przełącznik kompilatora [/Zc: externConstexpr](../build/reference/zc-externconstexpr.md) włącza poprawne standardy — zgodność z zachowaniem. Ostatecznie opcja stanie się wartością domyślną. Opcja [/permissive-](../build/reference/permissive-standards-conformance.md) nie włącza **/Zc: externConstexpr**.

```cpp
extern constexpr int x = 10; //error LNK2005: "int const x" already defined
```

Jeśli plik nagłówkowy zawiera zmienną zadeklarowaną **extern** **constexpr** , musi ona być oznaczona `__declspec(selectany)`, aby poprawnie mieć zduplikowane deklaracje:

```cpp
extern constexpr __declspec(selectany) int x = 10;
```

## <a name="opno-locextern-c-and-opno-locextern-c-function-declarations"></a>extern deklaracje funkcji "C"C++i extern ""

W C++programie, gdy jest używany z ciągiem, **extern** określa, że stosowane są konwencje łączenia innego języka dla deklarator. Funkcje i dane języka c są dostępne tylko wtedy, gdy są one wcześniej zadeklarowane jako posiadające powiązanie C. Jednak muszą być zdefiniowane w oddzielnie skompilowanej jednostce translacji.

Firma C++ Microsoft obsługuje ciągi **"C"** i **"C++"** w polu *literał ciągu* . Wszystkie standardowe pliki dołączane używają składni **extern "C"** , aby zezwalać na używanie funkcji biblioteki wykonawczej w C++ programach.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak zadeklarować nazwy, które mają połączenie C:

```cpp
// Declare printf with C linkage.
extern "C" int printf(const char *fmt, ...);

//  Cause everything in the specified
//  header files to have C linkage.
extern "C" {
    // add your #include statements here
#include <stdio.h>
}

//  Declare the two functions ShowChar
//  and GetChar with C linkage.
extern "C" {
    char ShowChar(char ch);
    char GetChar(void);
}

//  Define the two functions
//  ShowChar and GetChar with C linkage.
extern "C" char ShowChar(char ch) {
    putchar(ch);
    return ch;
}

extern "C" char GetChar(void) {
    char ch;
    ch = getchar();
    return ch;
}

// Declare a global variable, errno, with C linkage.
extern "C" int errno;
```

Jeśli funkcja ma więcej niż jedną specyfikację powiązania, muszą one wyrazić zgodę. Wystąpił błąd podczas deklarowania funkcji jako zarówno C, jak C++ i powiązania. Ponadto, jeśli dwie deklaracje dla funkcji występują w programie — jedna ze specyfikacją powiązania i jedna bez niej — deklaracja ze specyfikacją powiązania musi być pierwsza. Wszystkim nadmiarowym deklaracjom funkcji, które mają już specyfikację, nadawane są specyfikacje powiązania określone w pierwszej deklaracji. Na przykład:

```cpp
extern "C" int CFunc1();
...
int CFunc1();            // Redeclaration is benign; C linkage is
                         //  retained.

int CFunc2();
...
extern "C" int CFunc2(); // Error: not the first declaration of
                         //  CFunc2;  cannot contain linkage
                         //  specifier.
```

## <a name="see-also"></a>Zobacz także

[Keywords](../cpp/keywords-cpp.md)\
[Jednostki tłumaczenia i powiązania](program-and-linkage-cpp.md)\
[extern specyfikator klasy magazynu w języku C](../c-language/extern-storage-class-specifier.md)\
[Zachowanie identyfikatorów w języku C](../c-language/behavior-of-identifiers.md)\
[Połączenie w języku C](../c-language/linkage.md)
