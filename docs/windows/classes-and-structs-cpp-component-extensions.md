---
title: Klasy i struktury (C++ Component Extensions) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- ref class keyword [C++]
- value class keyword [C++]
- value struct keyword [C++]
- ref struct keyword [C++]
ms.assetid: 5c360764-b229-49c6-9357-66213afbc372
caps.latest.revision: "32"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8d75bc7f0935ef7444d37f3708379598a549417e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="classes-and-structs--c-component-extensions"></a>Klasy i struktury (C++ Component Extensions)
Deklaruje klasie lub strukturze których *okres istnienia obiektu* podawana jest automatycznie. Gdy obiekt nie jest już dostępny lub poza zakresem, Visual C++ spowoduje odrzucenie na pamięci, która jest przydzielona do obiektu.  
  
## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze  
 **Składnia**  
  
```  
  
      class_access  
      ref class  
      name  
      modifier :  inherit_accessbase_type {};  
class_accessref structnamemodifier :  inherit_accessbase_type {};  
class_accessvalue classnamemodifier :  inherit_accessbase_type {};  
class_accessvalue structnamemodifier :  inherit_accessbase_type {};  
  
```  
  
 **Parametry**  
  
 *class_access* (opcjonalnie)  
 Dostępność klasie lub strukturze poza zestaw. Możliwe wartości to **publicznego** i `private` (`private` jest ustawieniem domyślnym). Zagnieżdżone klasy lub struktury nie mogą mieć *class_access* specyfikator.  
  
 *Nazwa*  
 Nazwa klasy lub struktury.  
  
 *Modyfikator* (opcjonalnie)  
 [abstrakcyjna](../windows/abstract-cpp-component-extensions.md) i [zapieczętowanego](../windows/sealed-cpp-component-extensions.md) są prawidłowe modyfikatorów.  
  
 *inherit_access* (opcjonalnie)  
 Dostępność `base_type`. Tylko dostępność dozwolonych jest `public` (`public` jest ustawieniem domyślnym).  
  
 *base_type* (opcjonalnie)  
 Typ podstawowy. Jednak typ wartości nie może działać jako typu podstawowego.  
  
 Aby uzyskać więcej informacji zobacz opisy specyficzny dla języka tego parametru środowiska wykonawczego systemu Windows i Runtimesections języka wspólnego.  
  
 **Uwagi**  
  
 Dostępność elementu członkowskiego domyślnego obiektu zadeklarowana z **klasy referencyjnej** lub **klasę wartości** jest `private`. I dostępność elementu członkowskiego domyślnego obiektu zadeklarowana z **ref struct** lub **struktury wartość** jest `public`.  
  
 Gdy typ referencyjny z innego typu odwołania, jawnie musi zostać zastąpiona funkcji wirtualnych w klasie podstawowej (z [zastąpienia](../windows/override-cpp-component-extensions.md)), czy ukryty (z [new (nowe gniazdo w vtable)](../windows/new-new-slot-in-vtable-cpp-component-extensions.md)). Funkcje klasy pochodnej również muszą być jawnie oznaczone jako `virtual`.  
  
 Aby wykryć w czasie kompilacji, czy typ jest `ref class` lub `ref struct`, lub `value class` lub `value struct`, użyj `__is_ref_class (type)`, `__is_value_class (type)`, lub `__is_simple_value_class (type)`. Aby uzyskać więcej informacji, zobacz [Obsługa cech typu w kompilatorze](../windows/compiler-support-for-type-traits-cpp-component-extensions.md).  
  
 Aby uzyskać więcej informacji dotyczących klas i struktur zobacz  
  
-   [Utworzenie wystąpienia klasy i struktury](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md)  
  
 
  
-   [Semantyka stosu języka C++ dla typów odwołań](../dotnet/cpp-stack-semantics-for-reference-types.md)  
  
-   [Klas, struktur i Unii](../cpp/classes-and-structs-cpp.md)  
  
-   [Destruktory i finalizatory w porady: Definiowanie oraz stosowanie klas i struktur (C + +/ CLI)](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)  
  
-   [Operatory zdefiniowane przez użytkownika (C++/CLI)](../dotnet/user-defined-operators-cpp-cli.md)  
  
-   [Konwersje zdefiniowane przez użytkownika (C++/CLI)](../dotnet/user-defined-conversions-cpp-cli.md)  
  
-   [Instrukcje: opakowywanie klasy natywnej do użycia w języku C#](../dotnet/how-to-wrap-native-class-for-use-by-csharp.md)  
  
-   [Klasy ogólne [C++/CLI]](../windows/generic-classes-cpp-cli.md)  
  
## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows  
 **Uwagi**  
  
 Zobacz [Ref klas i struktur](http://msdn.microsoft.com/library/windows/apps/hh699870.aspx) i [wartość klas i struktur](http://msdn.microsoft.com/library/windows/apps/hh699861.aspx).  
  
 **Parametry**  
  
 *base_type* (opcjonalnie)  
 Typ podstawowy. A `ref class` lub `ref struct` może dziedziczyć zero lub więcej interfejsów i zero lub jeden `ref` typów. A `value class` lub `value struct` może dziedziczyć tylko zero lub więcej interfejsów.  
  
 Gdy deklarowanie obiektu za pomocą `ref class` lub `ref struct` słów kluczowych, obiekt jest dostępny przez dojście do obiektu; oznacza to, że wskaźnik licznika odwołanie do obiektu. Zadeklarowana zmienna odbędzie się poza zakresem, kompilator automatycznie usuwa obiekt źródłowy. Gdy obiekt jest używany jako parametr w wywołaniu lub jest przechowywana w zmiennej, uchwyt do obiektu jest rzeczywiście przekazany lub przechowywane.  
  
 Gdy deklarowanie obiektu za pomocą `value class` lub `value struct` słów kluczowych, okres istnienia obiektu zadeklarowane obiektu nie jest nadzorowane. Obiekt jest podobnie jak inne standard C++ klasy lub struktury.  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora: **/ZW**  
  
## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania 
 **Uwagi**  
  
 W poniższej tabeli wymieniono różnice składni pokazano **wszystkich środowisk uruchomieniowych** sekcji, które są specyficzne dla języka C + +/ CLI.  
  
 **Parametry**  
  
 *base_type* (opcjonalnie)  
 Typ podstawowy. A `ref class` lub `ref struct` może dziedziczyć zero lub więcej zarządzane interfejsy i zero lub jeden ref typów. A `value class` lub `value struct` może dziedziczyć tylko zero lub więcej interfejsów zarządzanych.  
  
 `ref class` i `ref struct` słowa kluczowe Poinformuj kompilator, który ma zostać przydzielone na stercie klasy lub struktury. Gdy obiekt jest używany jako parametr w wywołaniu lub jest przechowywana w zmiennej, odwołanie do obiektu jest rzeczywiście przekazany lub przechowywane.  
  
 `value class` i `value struct` słowa kluczowe informuje kompilator, że wartość przydzielone klasy lub struktury jest przekazany do funkcji lub przechowywane w elementach członkowskich.  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora:   **/CLR**  
  
## <a name="see-also"></a>Zobacz też  
 [Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)