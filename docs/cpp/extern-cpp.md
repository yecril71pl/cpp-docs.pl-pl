---
title: extern (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/12/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- extern
- extern_CPP
dev_langs:
- C++
helpviewer_keywords:
- extern keyword [C++], linkage to non-C++ functions
- declarations, external
- external linkage, extern modifier
ms.assetid: 1e2f0ae3-ae98-4410-85b5-222d6abc865a
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 00b9f94d02443163f45b83d64702fe49622597cd
ms.sourcegitcommit: d06966efce25c0e66286c8047726ffe743ea6be0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2018
ms.locfileid: "36238764"
---
# <a name="extern-c"></a>extern (C++)

**Extern** — słowo kluczowe jest stosowany do globalnej deklaracji zmiennej, function lub szablon do określenia, czy nazwa ten element ma *połączenie zewnętrzne*. Aby uzyskać ogólne informacje na połączenie i dlaczego nie jest zalecane używanie zmiennych globalnych, zobacz [Program i połączenie](program-and-linkage-cpp.md).

**Extern** — słowo kluczowe ma cztery znaczenia w zależności od kontekstu:

1. w globalnej deklaracji zmiennej wartością stałą **extern** Określa, że zmienną lub funkcję, jest zdefiniowany w innej jednostce tłumaczenia. **Extern** muszą być stosowane we wszystkich plikach, z wyjątkiem tego, gdzie zmienna jest zdefiniowana.
1. w deklaracji zmiennej stałej Określa on, że zmienna ma połączenie zewnętrzne. **Extern** należy zastosować do wszystkie deklaracje we wszystkich plikach. (Zmienne globalne const mieć powiązania wewnętrznego domyślnie).
1. **zewnętrzne "C"** Określa, że funkcja jest zdefiniowany w innym miejscu i używa konwencji wywoływania języka C. Extern — modyfikator "C" może być również stosowany do wielu deklaracje funkcji w bloku.
1. w deklaracji szablonu określa ona, że szablon utworzono już wystąpienie w innym miejscu. Jest to Optymalizacja oferująca informuje kompilator, że jej ponownego użycia innych wystąpienia zamiast tworzenia nowej w bieżącej lokalizacji. Aby uzyskać więcej informacji o tym **extern**, zobacz [szablony](templates-cpp.md).

## <a name="extern-linkage-for-non-const-globals"></a>połączenie zewnętrzne dla globals z systemem innym niż stała

Gdy widzi konsolidator **extern** przed deklaracji zmiennej globalnej szuka definicji w innej jednostce tłumaczenia. Deklaracje zmiennych z systemem innym niż stała w zakresie globalnym są zewnętrzne domyślnie; mają zastosowanie tylko **extern** deklaracje, które nie udostępniają definicji.

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

## <a name="extern-linkage-for-const-globals"></a>połączenie zewnętrzne dla const globals

A **const** — zmienna globalna ma połączenie zewnętrzne domyślnie. Jeśli chcesz mieć zewnętrzne połączenie w zmiennej, zastosuj **extern** — słowo kluczowe do definicji również, aby wszystkie deklaracje w innych plikach:

```cpp
//fileA.cpp
extern const int i = 42; // extern const definition

//fileB.cpp
extern const int i;  // declaration only. same as i in FileA
```

## <a name="extern-constexpr-linkage"></a>Zewnętrzne połączenie constexpr

W Visual Studio 2017 wersji 15.3 lub starszej kompilator zawsze udzielił constexpr zmiennej połączenie wewnętrzne nawet wtedy, gdy zmienna została oznaczona jako zewnętrzny. W Visual Studio 2017 wersji 15,5 cala, nowy przełącznik ([/Zc:externConstexpr](../build/reference/zc-externconstexpr.md)) umożliwia poprawne zachowanie zgodnych standardów. Po pewnym czasie będzie to wartość domyślna.

```cpp
extern constexpr int x = 10; //error LNK2005: "int const x" already defined
```

Jeśli plik nagłówka zawiera constexpr zmiennych extern zadeklarowane, musi być oznaczony **__declspec(selectany)** Aby poprawnie zawierać jego deklaracji zduplikowanych połączone:

```cpp
extern constexpr __declspec(selectany) int x = 10;
```

## <a name="extern-c-and-extern-c-function-declarations"></a>deklaracje funkcji zewnętrzne "C" i "C++" extern

 W języku C++, gdy jest używany z ciągiem **extern** Określa, czy dla declarator(s) są używane konwencje powiązanie dla innego języka. Funkcje języka C i dane są dostępne tylko wtedy, gdy wcześniej zostały zgłoszone jako mających powiązanie C. Jednak muszą być zdefiniowane w jednostce tłumaczenia oddzielnie skompilowany.

 Microsoft C++ obsługuje ciągi **"C"** i **"C++"** w *literał ciągu* pola. Wszystkie standardowe obejmują użycie plików **extern** składni "C", aby umożliwić funkcji biblioteki wykonawczej języka używanego w programach języka C++.

## <a name="example"></a>Przykład

Poniższy przykład przedstawia sposób zadeklarować nazwy, które mają powiązanie C:

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

## <a name="see-also"></a>Zobacz też

- [Słowa kluczowe](../cpp/keywords-cpp.md)
- [Program i połączenie](program-and-linkage-cpp.md)
- [extern Specyfikator klasy magazynu w języku C](../c-language/extern-storage-class-specifier.md) 
- [Zachowanie identyfikatorów w języku C](../c-language/behavior-of-identifiers.md) 
- [Połączenie w języku C](../c-language/linkage.md)