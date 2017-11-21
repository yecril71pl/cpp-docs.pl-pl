---
title: "Deklaracja zarządzanego typu klasy | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 182cb637351f722677d8da97c7a7b880c3241311
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="declaration-of-a-managed-class-type"></a>Deklaracja zarządzanego typu klasy
Sposób, aby zadeklarować typu klasy odwołania zmieniła się z rozszerzeń zarządzanych dla języka C++ dla Visual C++.  
  
 W zarządzanych rozszerzeń typu klasy odwołania jest poprzedzone znakiem `__gc` — słowo kluczowe. W nowej składni `__gc` — słowo kluczowe jest zastępowany przez jedną z dwóch rozmieszczonych w odległości słów kluczowych: `ref class` lub `ref struct`. Wybór `struct` lub `class` wskazuje publicznego (dla `struct`) lub prywatnej (dla `class`) domyślny poziom dostępu do jego elementów członkowskich zadeklarowane w początkowej sekcji pojedyncza jednostka typu.  
  
 Podobnie, w zarządzanych rozszerzeń typu klasy wartości jest poprzedzone znakiem `__value` — słowo kluczowe. W nowej składni `__value` — słowo kluczowe jest zastępowany przez jedną z dwóch rozmieszczonych w odległości słów kluczowych: `value class` lub `value struct`.  
  
 Typ interfejsu w zarządzanych rozszerzeń wskazano ze słowem kluczowym `__interface`. W nowej składni, zostanie zastąpiony wartością `interface class`.  
  
 Na przykład następujące klasy deklaracje w zarządzanych rozszerzeń:  
  
```  
public __gc class Block {};     // reference class  
public __value class Vector {}; // value class  
public __interface IFooBar {};  // interface class  
```  
  
 W obszarze nowej składni te ekwiwalentnie został zadeklarowany w następujący sposób:  
  
```  
public ref class Block {};         // reference class  
public value class Vector {};      // value class  
public interface class IFooBar {}; // interface class  
```  
  
## <a name="specifying-the-class-as-abstract"></a>Określenia klasy jako abstrakcyjny  
 W obszarze rozszerzeń zarządzanych umieść słowa kluczowego `__abstract` przed `class` — słowo kluczowe (przed lub po `__gc`) oznacza, że klasa jest niekompletne i czy obiekty klasy nie można utworzyć w programie:  
  
```  
public __gc __abstract class Shape {};  
public __gc __abstract class Shape2D: public Shape {};  
```  
  
 Po wybraniu nowej składni, można określić `abstract` kontekstowe słowo kluczowe po klasie nazwę i przed treści klasy, listy pochodnym klasy podstawowej lub średnikami.  
  
```  
public ref class Shape abstract {};  
public ref class Shape2D abstract : public Shape{};  
```  
  
 Oczywiście znaczenie semantyczne nie ulega zmianie.  
  
## <a name="specifying-the-class-as-sealed"></a>Określenia klasy jako zapieczętowany  
 W obszarze rozszerzeń zarządzanych umieść słowa kluczowego `__sealed` przed `class` — słowo kluczowe (przed lub po `__gc`) wskazująca, że obiekty klasy nie może być dziedziczona z:  
  
```  
public __gc __sealed class String {};  
```  
  
 Po wybraniu nowej składni, można określić `sealed` kontekstowe słowo kluczowe po klasie nazwę i przed treści klasy, listy pochodnym klasy podstawowej lub średnikami.  
  
 Można jednocześnie wyprowadzenia klasy i zapieczętuj go. Na przykład `String` niejawnie jest pochodną klasy `Object`. Zaletą pieczętowania klasy jest obsługa statycznej rozpoznawania (to znaczy w czasie kompilacji) wszystkich wywołań funkcji wirtualnej za pośrednictwem obiektu klasy zapieczętowanej odwołania. Jest to spowodowane `sealed` specyfikator gwarantuje, że `String` śledzenie uchwytu nie może odwoływać się do następnie pochodnej klasy, która może zapewnić wystąpienie nadrzędnych wirtualnych wywoływana metoda. Oto przykład klasy zapieczętowanej w nowej składni:  
  
```  
public ref class String sealed {};  
```  
  
 Jeden można również określić klasę jako zarówno abstrakcyjny i zapieczętowany — jest to specjalne warunek, który wskazuje klasy statycznej. To jest opisane w dokumentacji CLR w następujący sposób:  
  
 "A Typ zarówno `abstract` i `sealed` powinien mieć tylko statyczne elementy członkowskie i służy jako co w przypadku niektórych języków wywołać przestrzeni nazw."  
  
 Na przykład w tym miejscu jest deklaracja klasy abstrakcyjnej zapieczętowanego przy użyciu składni zarządzanych rozszerzeń:  
  
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
  
## <a name="clr-inheritance-specifying-the-base-class"></a>Dziedziczenie CLR: Określanie klasy podstawowej  
 W modelu obiektu CLR jest obsługiwany tylko publiczne dziedziczenie pojedynczego. Jednak rozszerzeń zarządzanych zachowywane ISO C++ domyślnej interpretacji klasy podstawowej bez słowa kluczowego dostępu jako określania prywatnych pochodnym. Oznacza to, że każda deklaracja dziedziczenia CLR zapewnienie `public` — słowo kluczowe w celu zastąpienia domyślnej interpretacji.  
  
```  
// Managed Extensions: error: defaults to private derivation  
__gc class Derived : Base {};  
```  
  
 W nowej definicji składni braku dostępu do — słowo kluczowe wskazuje publicznego pochodnym w definicji dziedziczenia CLR. W związku z tym `public` — słowo kluczowe dostępu teraz jest opcjonalne. Gdy ta sytuacja nie wymaga żadnych modyfikacji rozszerzeń zarządzanych dla kodu C++, wyświetlania tej zmiany tutaj aby informacje były kompletne.  
  
```  
// New syntax: ok: defaults to public derivation  
ref class Derived : Base{};  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Typy zarządzane (C + +/ CL)](../dotnet/managed-types-cpp-cl.md)   
 [Klasy i struktury](../windows/classes-and-structs-cpp-component-extensions.md)   
 [abstrakcyjny](../windows/abstract-cpp-component-extensions.md)   
 [zapieczętowane](../windows/sealed-cpp-component-extensions.md)