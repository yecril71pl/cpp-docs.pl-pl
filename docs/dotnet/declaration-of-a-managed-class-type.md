---
title: Deklaracja zarządzanego typu klasy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- __gc types
- classes [C++], managed
- class keyword [C++], CLR
- __value keyword
- value types, declaring
- value keyword [C++]
- managed classes
- interface class keyword
- ref keyword [C++]
ms.assetid: 16de9c94-91d7-492f-8ac7-f0729cc627e9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 0f9ceb0867fbdfbbdb46075662fca802d1ee0bba
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46393675"
---
# <a name="declaration-of-a-managed-class-type"></a>Deklaracja zarządzanego typu klasy

Sposób, aby zadeklarować typ klasy odwołania zmieniła się z zarządzanych rozszerzeń dla C++ do Visual C++.

W zarządzanych rozszerzeń typ klasy odwołania jest poprzedzony elementem `__gc` — słowo kluczowe. W nowej składni `__gc` — słowo kluczowe jest zastępowany przez jedną z dwóch odstępów między słowami kluczowymi: `ref class` lub `ref struct`. Wybór `struct` lub `class` wskazuje publicznej (dla `struct`) lub prywatnej (dla `class`) domyślny poziom dostępu do składowych zadeklarowanych w początkowej bez etykiety części treści tego typu.

Podobnie, w zarządzanych rozszerzeń typu klasy wartości jest poprzedzony elementem `__value` — słowo kluczowe. W nowej składni `__value` — słowo kluczowe jest zastępowany przez jedną z dwóch odstępów między słowami kluczowymi: `value class` lub `value struct`.

Typ interfejsu, w zarządzanych rozszerzeń wskazano ze słowem kluczowym `__interface`. W nowej składni, zostanie zastąpiony wartością `interface class`.

Na przykład następujące deklaracje klas w zarządzanych rozszerzeń:

```
public __gc class Block {};     // reference class
public __value class Vector {}; // value class
public __interface IFooBar {};  // interface class
```

W ramach nowej składni te są ekwiwalentnie zadeklarowane w następujący sposób:

```
public ref class Block {};         // reference class
public value class Vector {};      // value class
public interface class IFooBar {}; // interface class
```

## <a name="specifying-the-class-as-abstract"></a>Określanie klasy jako abstrakcyjnej

W obszarze zarządzanych rozszerzeń, umieść słowa kluczowego `__abstract` przed `class` — słowo kluczowe (przed lub po `__gc`) oznacza, że klasa jest niekompletna i czy obiekty klasy nie można utworzyć w ramach programu:

```
public __gc __abstract class Shape {};
public __gc __abstract class Shape2D: public Shape {};
```

Po wybraniu nowej składni można określić `abstract` kontekstowego słowa kluczowego, zgodnie z nazwą klasy i przed treści klasy, lista pochodnym klasy bazowej lub średnikami.

```
public ref class Shape abstract {};
public ref class Shape2D abstract : public Shape{};
```

Oczywiście znaczenia semantycznego ulega zmianie.

## <a name="specifying-the-class-as-sealed"></a>Określanie klasy jako zapieczętowany

W obszarze zarządzanych rozszerzeń, umieść słowa kluczowego `__sealed` przed `class` — słowo kluczowe (przed lub po `__gc`) do wskazania, że obiekty klasy nie może być dziedziczona z:

```
public __gc __sealed class String {};
```

Po wybraniu nowej składni można określić `sealed` kontekstowego słowa kluczowego, zgodnie z nazwą klasy i przed treści klasy, lista pochodnym klasy bazowej lub średnikami.

Można wyprowadzić klasę lub zapieczętuj go. Na przykład `String` klasy niejawnie pochodzi od `Object`. Zaletą pieczętowania klasy jest Obsługa rozwiązania statyczne (oznacza to, w czasie kompilacji) dla wszystkich wywołań funkcji wirtualnych za pośrednictwem obiektu klasy odwołania zapieczętowany. Jest to spowodowane `sealed` specyfikator gwarantuje, że `String` śledzenie uchwytu nie może odwoływać się do następnie pochodnej klasy, która może zapewnić wystąpienie nadrzędnych wirtualnych wywoływana metoda. Oto przykład klasy zapieczętowanej w nowej składni:

```
public ref class String sealed {};
```

Jeden można również określić klasę jako abstrakcyjny zarówno i zapieczętowany — jest to specjalny warunek, który wskazuje klasy statycznej. Jest to opisane w dokumentacji środowiska CLR w następujący sposób:

"A Typ zarówno `abstract` i `sealed` powinni mieć tylko statyczne elementy członkowskie, i służy jako co w przypadku niektórych języków wywołania przestrzeni nazw."

Na przykład poniżej przedstawiono deklarację zapieczętowana klasa abstrakcyjna przy użyciu składni zarządzanych rozszerzeń:

```
public __gc __sealed __abstract class State {
public:
   static State() {}
   static bool inParamList();

private:
   static bool ms_inParam;
};
```

a Oto tej deklaracji przetłumaczyć nowej składni:

```
public ref class State abstract sealed {
public:
   static State();
   static bool inParamList();

private:
   static bool ms_inParam;
};
```

## <a name="clr-inheritance-specifying-the-base-class"></a>Dziedziczenie CLR: Określanie klasy bazowej

W modelu obiektu CLR publiczne pojedyncze dziedziczenie jest obsługiwane. Jednak zarządzanych rozszerzeń zachowane ISO C++ domyślna interpretacja klasę bazową bez słowa kluczowego dostępu, co określenie typem pochodnym prywatnych. Oznacza to, że każda deklaracja dziedziczenia CLR zapewnienie `public` — słowo kluczowe do zastąpienia domyślnej interpretacji kodów.

```
// Managed Extensions: error: defaults to private derivation
__gc class Derived : Base {};
```

W nowej definicji składni braku — słowo kluczowe dostępu wskazuje typem pochodnym publicznych w definicji dziedziczenia CLR. W efekcie `public` dostępu — słowo kluczowe jest teraz opcjonalny. Gdy to nie wymaga żadnych modyfikacji zarządzanych rozszerzeń dla kodu C++, mogę wyświetlić tę zmianę, w tym miejscu aby informacje były kompletne.

```
// New syntax: ok: defaults to public derivation
ref class Derived : Base{};
```

## <a name="see-also"></a>Zobacz też

[Typy zarządzane (C + +/ CL)](../dotnet/managed-types-cpp-cl.md)<br/>
[Klasy i struktury](../windows/classes-and-structs-cpp-component-extensions.md)<br/>
[abstract](../windows/abstract-cpp-component-extensions.md)<br/>
[sealed](../windows/sealed-cpp-component-extensions.md)