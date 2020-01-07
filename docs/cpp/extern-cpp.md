---
title: extern (C++)
ms.date: 04/12/2018
f1_keywords:
- extern
- extern_CPP
helpviewer_keywords:
- extern keyword [C++], linkage to non-C++ functions
- declarations, external
- external linkage, extern modifier
ms.assetid: 1e2f0ae3-ae98-4410-85b5-222d6abc865a
ms.openlocfilehash: d42a32202f7fa67751ea36757c13b2c6af4953b2
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301538"
---
# <a name="extern-c"></a>extern (C++)

Słowo kluczowe **extern** jest stosowane do zmiennej globalnej, funkcji lub deklaracji szablonu, aby określić, że nazwa tego elementu ma *połączenie zewnętrzne*. Aby uzyskać ogólne informacje na temat powiązania i dlaczego nie zaleca się używania zmiennych globalnych, zobacz [jednostki translacji i powiązania](program-and-linkage-cpp.md).

Słowo kluczowe **extern** ma cztery znaczenia w zależności od kontekstu:

1. w deklaracji zmiennej globalnej innej niż stała, **extern** określa, że zmienna lub funkcja jest zdefiniowana w innej jednostce tłumaczenia. **Extern** należy zastosować we wszystkich plikach, z wyjątkiem tego, gdzie zmienna jest zdefiniowana.
1. w deklaracji zmiennej const określa, że zmienna ma powiązania zewnętrzne. **Extern** należy zastosować do wszystkich deklaracji we wszystkich plikach. (Globalne zmienne stałe mają domyślnie powiązania wewnętrzne).
1. **extern "C"** określa, że funkcja jest zdefiniowana w innym miejscu i używa konwencji wywoływania języka C. Zewnętrzny modyfikator "C" może być również stosowany do wielu deklaracji funkcji w bloku.
1. w deklaracji szablonu określa, że szablon został już skonkretyzowany w innym miejscu. Jest to Optymalizacja, która informuje kompilator, że może odnowić użycie innych wystąpień zamiast tworzyć nowe w bieżącej lokalizacji. Aby uzyskać więcej informacji o tym, jak używać **extern**, zobacz [templates](templates-cpp.md).

## <a name="extern-linkage-for-non-const-globals"></a>powiązanie extern dla nieconst Globals

Gdy konsolidator widzi **extern** przed deklaracją zmiennej globalnej, szuka definicji w innej jednostce tłumaczenia. Deklaracje zmiennych innych niż const w zakresie globalnym są domyślnie zewnętrzne. Zastosuj **extern** tylko do deklaracji, które nie zawierają definicji.

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

## <a name="extern-linkage-for-const-globals"></a>połączenie extern dla elementu const Globals

Zmienna globalna **const** ma domyślnie powiązania wewnętrzne. Jeśli chcesz, aby zmienna miała powiązanie zewnętrzne, Zastosuj słowo kluczowe **extern** do definicji, a także do wszystkich innych deklaracji w innych plikach:

```cpp
//fileA.cpp
extern const int i = 42; // extern const definition

//fileB.cpp
extern const int i;  // declaration only. same as i in FileA
```

## <a name="extern-constexpr-linkage"></a>zewnętrzny związek constexpr

W programie Visual Studio 2017 w wersji 15,3 lub starszej kompilator zawsze otrzymał zmienną constexpr, która jest połączeniem wewnętrznym, nawet gdy zmienna została oznaczona jako extern. W programie Visual Studio 2017 w wersji 15,5 nowy przełącznik kompilatora ([/Zc: externConstexpr](../build/reference/zc-externconstexpr.md)) włącza poprawne standardy — zgodność z zachowaniem. Ostatecznie stanie się to ustawieniem domyślnym. Opcja/permissive-nie włącza/Zc: externConstexpr.

```cpp
extern constexpr int x = 10; //error LNK2005: "int const x" already defined
```

Jeśli plik nagłówkowy zawiera zmienną zadeklarowaną jako extern constexpr, należy ją oznaczyć **__declspec (selectany)** w celu poprawnego podzielenia zduplikowanych deklaracji:

```cpp
extern constexpr __declspec(selectany) int x = 10;
```

## <a name="extern-c-and-extern-c-function-declarations"></a>Deklaracje funkcji extern "C"C++i "extern" "

W C++programie, gdy jest używany z ciągiem, **extern** określa, że stosowane są konwencje łączenia innego języka dla deklarator. Funkcje i dane języka c są dostępne tylko wtedy, gdy zostały zadeklarowane wcześniej jako posiadające powiązanie C. Jednak muszą być zdefiniowane w oddzielnie skompilowanej jednostce translacji.

Firma C++ Microsoft obsługuje ciągi **"C"** i **"C++"** w polu *literał ciągu* . Wszystkie standardowe pliki dołączane używają składni **extern** "C", aby zezwalać na używanie funkcji biblioteki wykonawczej w C++ programach.

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

Jeśli funkcja ma więcej niż jedną specyfikację powiązania, muszą być zgodne; błędem jest deklaracja funkcji jako posiadających powiązania C i C++. Ponadto, jeśli dwie deklaracje dla funkcji występują w programie — jedna ze specyfikacją powiązania i jedna bez niej — deklaracja ze specyfikacją powiązania musi być pierwsza. Wszystkim nadmiarowym deklaracjom funkcji, które mają już specyfikację, nadawane są specyfikacje powiązania określone w pierwszej deklaracji. Na przykład:

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

[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[Jednostki tłumaczenia i powiązania](program-and-linkage-cpp.md)<br/>
[zewnętrzny specyfikator klasy magazynu w języku C](../c-language/extern-storage-class-specifier.md)<br/>
[Zachowanie identyfikatorów w języku C](../c-language/behavior-of-identifiers.md)<br/>
[Połączenie w języku C](../c-language/linkage.md)