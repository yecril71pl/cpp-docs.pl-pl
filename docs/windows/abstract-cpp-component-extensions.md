---
title: abstract (C + +/ CLI i C + +/ CX) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- abstract
- abstract_cpp
dev_langs:
- C++
helpviewer_keywords:
- abstract keyword [C++]
ms.assetid: cbae3408-0378-4ac8-b70d-c016b381a6d5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 78a5b42de6b0ac54d060bb6369566aa446863289
ms.sourcegitcommit: 3f4e92266737ecb70507871e87dc8e2965ad7e04
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2018
ms.locfileid: "49328197"
---
# <a name="abstract--ccli-and-ccx"></a>abstract (C + +/ CLI i C + +/ CX)

**Abstrakcyjne** — słowo kluczowe deklaruje albo:

- Typ może być używany jako typ podstawowy, ale nie można utworzyć wystąpienia samego typu.

- Funkcja składowa typu można zdefiniować tylko w typie pochodnym.

## <a name="all-platforms"></a>Wszystkie platformy

### <a name="syntax"></a>Składnia

*Deklaracja klasy* *identyfikator klasy* **abstrakcyjne {}**

**wirtualne** *zwracanego typu* *identyfikator w przypadku funkcji elementu członkowskiego* **abstrakcyjny ();**

### <a name="remarks"></a>Uwagi

Pierwszy składni przykład deklaruje klasa może być abstrakcyjna. *Deklaracji klasy* składnik może być natywna deklaracja C++ (**klasy** lub **struktury**), lub deklaracja rozszerzenie języka C++ (**klasy referencyjnej** lub **ref struct**) Jeśli `/ZW` lub `/clr` określono opcję kompilatora.

Drugi składni przykład deklaruje wirtualnej funkcji składowej jako abstrakcyjny. Deklarowanie abstrakcyjnej funkcji jest taka sama jak deklarując jej czystej funkcji wirtualnej. Deklarowanie abstrakcyjna funkcja elementu członkowskiego również powoduje, że otaczającej klasy, która ma być zadeklarowany jako abstrakcyjny.

**Abstrakcyjne** — słowo kluczowe jest obsługiwane w kodzie macierzystym i specyficzne dla platformy; oznacza to, może być kompilowane z lub bez `/ZW` lub `/clr` — opcja kompilatora.

Można wykrywać w czasie kompilacji, jeśli typ jest abstrakcyjny z `__is_abstract(type)` cechy typu. Aby uzyskać więcej informacji, zobacz [Obsługa cech typu w kompilatorze](../windows/compiler-support-for-type-traits-cpp-component-extensions.md).

**Abstrakcyjne** — słowo kluczowe jest specyfikator przesłonięcia kontekstowej. Aby uzyskać więcej informacji na temat kontekstowych słów kluczowych, zobacz [Context-Sensitive Keywords](../windows/context-sensitive-keywords-cpp-component-extensions.md). Aby uzyskać więcej informacji na temat nadpisania specyfikatorów, zobacz [porady: deklarowanie specyfikatorów zastąpienia w kompilacjach kodu natywnego](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md).

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

Aby uzyskać więcej informacji, zobacz [klasy i struktury odwołania](../cppcx/ref-classes-and-structs-c-cx.md).

### <a name="requirements"></a>Wymagania

— Opcja kompilatora: `/ZW`

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

### <a name="requirements"></a>Wymagania

— Opcja kompilatora: `/clr`

### <a name="examples"></a>Przykłady

Poniższy kod generuje błąd, ponieważ klasa `X` jest oznaczony jako **abstrakcyjne**.

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

Poniższy kod generuje błąd, ponieważ tworzenia wystąpienia klasy natywnej, która jest oznaczona **abstrakcyjne**. Ten błąd wystąpi, z lub bez `/clr` — opcja kompilatora.

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

Poniższy kod generuje błąd, ponieważ funkcja `f` zawiera definicję, ale jest oznaczony **abstrakcyjne**. Końcowe zestawienie w przykładzie pokazuje, że deklarowania funkcji wirtualnych abstrakcyjnej równoważne do deklarowania czystej funkcji wirtualnej.

```cpp
// abstract_keyword_3.cpp
// compile with: /clr
ref class X {
public:
   virtual void f() abstract {}   // C3634
   virtual void g() = 0 {}   // C3634
};
```

## <a name="see-also"></a>Zobacz też

[Component Extensions dla platformy .NET i platformy uniwersalnej systemu Windows](../windows/component-extensions-for-runtime-platforms.md)
