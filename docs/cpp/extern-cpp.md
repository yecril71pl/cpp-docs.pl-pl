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
ms.openlocfilehash: 4a3a4e158794e06f28c638e87e014ddc3fb99837
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50648724"
---
# <a name="extern-c"></a>extern (C++)

**Extern** — słowo kluczowe jest stosowany do globalnego deklaracji zmiennej, funkcja lub szablon do określenia, czy nazwa to coś ma *powiązania zewnętrzne*. Aby uzyskać ogólne informacje dotyczące powiązania i dlaczego zaleca się użycie zmiennych globalnych, zobacz [Program i połączenie](program-and-linkage-cpp.md).

**Extern** — słowo kluczowe ma cztery znaczenie w zależności od kontekstu:

1. w globalnej deklaracji zmiennej niestały **extern** Określa, że zmienna lub funkcja jest zdefiniowana w innej jednostce translacji. **Extern** muszą być stosowane we wszystkich plikach, z wyjątkiem tego, gdzie zmienna jest zdefiniowana.
1. w deklaracji zmiennej const określa to, że zmienna ma powiązania zewnętrzne. **Extern** muszą być stosowane do wszystkich deklaracji we wszystkich plikach. (Zmienne globalne const musi zewnętrzne domyślnie).
1. **extern "C"** Określa, że funkcja jest zdefiniowana w innym miejscu, a następnie używa konwencji wywoływania języka C. Modyfikator extern "C" mogą być również stosowane do wielu deklaracji funkcji w bloku.
1. w deklaracji szablonu określa ona, że szablon ma już wystąpienie gdzie indziej. Jest to optymalizacji, który informuje kompilator, że jej ponownego użycia innym wystąpieniem, zamiast tworzenia nowej w bieżącej lokalizacji. Aby uzyskać więcej informacji dotyczących używania tego **extern**, zobacz [szablony](templates-cpp.md).

## <a name="extern-linkage-for-non-const-globals"></a>powiązania zewnętrzne dla niestałe funkcje globalne

Gdy widzi konsolidator **extern** przed deklarację zmiennej globalnej szuka definicji w innej jednostce translacji. Deklaracje zmiennych o wartości innej niż stała w globalnym zakresie są zewnętrzne domyślnie; mają zastosowanie tylko **extern** deklaracje, które nie udostępniają definicji.

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

## <a name="extern-linkage-for-const-globals"></a>powiązania zewnętrzne dla const globals

A **const** zmienna globalna ma połączenie zewnętrzne domyślnie. W razie potrzeby zmienną mają powiązania zewnętrzne zastosować **extern** — słowo kluczowe do definicji również do innych deklaracji w innych plikach:

```cpp
//fileA.cpp
extern const int i = 42; // extern const definition

//fileB.cpp
extern const int i;  // declaration only. same as i in FileA
```

## <a name="extern-constexpr-linkage"></a>Extern constexpr powiązania

W Visual Studio 2017 w wersji 15.3 lub starszej kompilator zawsze nadaje powiązanie wewnętrzne zmiennej constexpr, nawet wtedy, gdy zmienna została oznaczona jako zewnętrzny. W programie Visual Studio 2017 w wersji 15.5, nowy przełącznik ([/Zc: externconstexpr](../build/reference/zc-externconstexpr.md)) umożliwia poprawne zachowanie zgodne z normami. Po pewnym czasie będzie to wartość domyślna.

```cpp
extern constexpr int x = 10; //error LNK2005: "int const x" already defined
```

Jeśli pliku nagłówka zawiera constexpr zmiennych zadeklarowanych zewnętrzne, musi być oznaczony **__declspec(selectany)** celu poprawnie jego deklaracji zduplikowanych połączone:

```cpp
extern constexpr __declspec(selectany) int x = 10;
```

## <a name="extern-c-and-extern-c-function-declarations"></a>deklaracje funkcji extern "C" i extern "C++"

W języku C++, gdy jest używana przy użyciu parametrów **extern** Określa, że declarator(s) używane są konwencje powiązania innego języka. Funkcje języka C i dane są dostępne tylko wtedy, gdy wcześniej są deklarowane jako mających powiązanie C. Jednak muszą być zdefiniowane w jednostce translacji oddzielnie skompilowane.

Microsoft C++ obsługuje ciągi **"C"** i **"C++"** w *literał ciągu* pola. Standardowa obejmują pliki, używają **extern** składni "C", aby umożliwić funkcji biblioteki wykonawczej, które mają być używane w programach języka C++.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje sposób deklarowania nazw, które mają powiązania C:

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
[Program i połączenie](program-and-linkage-cpp.md)<br/>
[extern — Specyfikator klasy magazynowania w języku C](../c-language/extern-storage-class-specifier.md)<br/>
[Zachowanie identyfikatory w języku C](../c-language/behavior-of-identifiers.md)<br/>
[Powiązania w języku C](../c-language/linkage.md)