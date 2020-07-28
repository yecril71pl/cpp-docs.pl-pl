---
title: abstract  (C++/CLI i C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- abstract
- abstract_cpp
helpviewer_keywords:
- abstract keyword [C++]
ms.assetid: cbae3408-0378-4ac8-b70d-c016b381a6d5
ms.openlocfilehash: 1e729589f78c56111717a87a27f9c7370dca7b90
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214298"
---
# <a name="abstract--ccli-and-ccx"></a>abstract  (C++/CLI i C++/CX)

**Abstrakcyjne** słowo kluczowe deklaruje:

- Typ może być używany jako typ podstawowy, ale nie można utworzyć wystąpienia samego typu.

- Funkcja członkowska typu może być zdefiniowana tylko w typie pochodnym.

## <a name="all-platforms"></a>Wszystkie platformy

### <a name="syntax"></a>Składnia

**abstrakcyjny {} ** *Identyfikator klasy* *deklaracji klasy*

**`virtual`***Typ zwracany* *elementu członkowskiego-identyfikatora funkcji* **()**

### <a name="remarks"></a>Uwagi

Pierwsza Przykładowa składnia deklaruje klasę jako abstrakcyjną. Składnik *deklaracji klasy* może być natywną deklaracją c++ (** `class` * * * * lub **`struct`** ) lub deklaracją rozszerzenia c++ (** Klasa ref * * lub **ref struct**), jeśli `/ZW` `/clr` określono opcję kompilatora lub.

Druga Przykładowa składnia deklaruje wirtualną funkcję członkowską, która ma być abstrakcyjna. Deklarowanie abstrakcyjnej funkcji jest takie samo jak deklarowanie jej czystej funkcji wirtualnej. Deklarowanie funkcji członkowskiej jako abstrakcyjnej powoduje również zadeklarowanie klasy otaczającej.

**Abstrakcyjne** słowo kluczowe jest obsługiwane w kodzie natywnym i specyficznym dla platformy; oznacza to, że można kompilować z lub bez `/ZW` `/clr` opcji kompilatora lub.

Można wykryć w czasie kompilacji, jeśli typ jest abstrakcyjny z `__is_abstract(type)` cechą typu. Aby uzyskać więcej informacji, zobacz [Obsługa kompilatora dla cech typu](compiler-support-for-type-traits-cpp-component-extensions.md).

**Abstrakcyjne** słowo kluczowe jest kontekstowym specyfikatorem przesłonięcia. Aby uzyskać więcej informacji na temat kontekstowych słów kluczowych, zobacz [kontekstowe słowa kluczowe](context-sensitive-keywords-cpp-component-extensions.md). Aby uzyskać więcej informacji na temat specyfikatorów przesłonięcia, zobacz [jak: deklarowanie specyfikatorów przesłonięć w kompilacjach natywnych](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md).

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

Aby uzyskać więcej informacji, zobacz [klasy referencyjne i struktury](../cppcx/ref-classes-and-structs-c-cx.md).

### <a name="requirements"></a>Wymagania

Opcja kompilatora:`/ZW`

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

### <a name="requirements"></a>Wymagania

Opcja kompilatora:`/clr`

### <a name="examples"></a>Przykłady

Poniższy przykład kodu generuje błąd, ponieważ Klasa `X` jest oznaczona jako **abstract**.

```cpp
// abstract_keyword.cpp
// compile with: /clr
ref class X abstract {
public:
   virtual void f() {}
};

int main() {
   X ^ MyX = gcnew X;   // C3622
}
```

Poniższy przykład kodu generuje błąd, ponieważ tworzy wystąpienie klasy natywnej, która jest oznaczona jako **abstract**. Ten błąd wystąpi z opcją kompilatora lub bez niej `/clr` .

```cpp
// abstract_keyword_2.cpp
class X abstract {
public:
   virtual void f() {}
};

int main() {
   X * MyX = new X; // C3622: 'X': a class declared as 'abstract'
                    // cannot be instantiated. See declaration of 'X'}
```

Poniższy przykład kodu generuje błąd, ponieważ funkcja `f` zawiera definicję, ale jest oznaczona jako **abstrakcyjna**. Końcowa instrukcja w przykładzie pokazuje, że deklarowanie abstrakcyjnej funkcji wirtualnej jest równoważne do deklarowania czystej funkcji wirtualnej.

```cpp
// abstract_keyword_3.cpp
// compile with: /clr
ref class X {
public:
   virtual void f() abstract {}   // C3634
   virtual void g() = 0 {}   // C3634
};
```

## <a name="see-also"></a>Zobacz także

[Rozszerzenia składników dla platform .NET i platformy UWP](component-extensions-for-runtime-platforms.md)
