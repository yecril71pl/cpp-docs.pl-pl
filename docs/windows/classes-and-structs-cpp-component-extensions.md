---
title: Klasy i struktury (C++ Component Extensions) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- ref class keyword [C++]
- value class keyword [C++]
- value struct keyword [C++]
- ref struct keyword [C++]
ms.assetid: 5c360764-b229-49c6-9357-66213afbc372
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 33fba76d39811b0fed777f057c5936a29f8c8a1a
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42595096"
---
# <a name="classes-and-structs--c-component-extensions"></a>Klasy i struktury (C++ Component Extensions)

Deklaruje klasie lub strukturze którego *okres istnienia obiektu* są zarządzane automatycznie. Gdy obiekt nie jest już dostępny, lub wykracza poza zakres, Visual C++ powoduje odrzucenie na pamięć, która jest przydzielona do obiektu.

## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze

### <a name="syntax"></a>Składnia

```cpp
      class_access
      ref class
      name
      modifier :  inherit_accessbase_type {};
class_accessref structnamemodifier :  inherit_accessbase_type {};
class_accessvalue classnamemodifier :  inherit_accessbase_type {};
class_accessvalue structnamemodifier :  inherit_accessbase_type {};

```

### <a name="parameters"></a>Parametry

*class_access* (opcjonalnie)  
Dostępność klasy lub struktury spoza zestawu. Możliwe wartości to **publicznych** i **prywatnej** (**prywatnej** jest ustawieniem domyślnym). Zagnieżdżone klasy lub struktury nie mogą mieć *class_access* specyfikator.

*Nazwa*  
Nazwa klasy lub struktury.

*Modyfikator* (opcjonalnie)  
[abstrakcyjna](../windows/abstract-cpp-component-extensions.md) i [zapieczętowanego](../windows/sealed-cpp-component-extensions.md) są prawidłowe modyfikatorów.

*inherit_access* (opcjonalnie)  
Dostępność *base_type*. Tylko dozwolone ułatwień dostępu jest **publicznych** (**publicznych** jest ustawieniem domyślnym).

*base_type* (opcjonalnie)  
Typ podstawowy. Jednak typ wartościowy nie może działać jako typu podstawowego.

Aby uzyskać więcej informacji zobacz opisy specyficzny dla języka tego parametru w Windows środowiska uruchomieniowego i typowych Runtimesections języka.

### <a name="remarks"></a>Uwagi

Wartość domyślna dostępu elementu członkowskiego obiektu zadeklarowane za pomocą **klasy referencyjnej** lub **klasę wartości** jest **prywatnej**. I ułatwienia dostępu członków domyślnego obiektu zadeklarowane za pomocą **ref struct** lub **struktury wartości** jest **publicznych**.

Gdy typ odwołania dziedziczy z innego typu odwołania, funkcje wirtualne w klasie bazowej jawnie musi zostać zastąpiona (przy użyciu [zastąpienia](../windows/override-cpp-component-extensions.md)) lub ukryte (przy użyciu [new (nowe gniazdo w vtable)](../windows/new-new-slot-in-vtable-cpp-component-extensions.md)). Funkcje klasy pochodnej musi również jawnie oznaczona jako **wirtualnego**.

Aby wykryć w czasie kompilacji, czy typ jest **klasy referencyjnej** lub **ref struct**, lub **klasę wartości** lub **struktury wartości**, użyj `__is_ref_class (type)`, `__is_value_class (type)`, lub `__is_simple_value_class (type)`. Aby uzyskać więcej informacji, zobacz [Obsługa cech typu w kompilatorze](../windows/compiler-support-for-type-traits-cpp-component-extensions.md).

Aby uzyskać więcej informacji na temat klas i struktur zobacz

- [Utworzenie wystąpienia klasy i struktury](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md)

- [Semantyka stosu języka C++ dla typów odwołań](../dotnet/cpp-stack-semantics-for-reference-types.md)

- [Klas, struktur i Unii](../cpp/classes-and-structs-cpp.md)

- [Destruktory i finalizatory w porady: Definiowanie oraz stosowanie klas i struktur (C + +/ CLI)](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)

- [Operatory zdefiniowane przez użytkownika (C++/CLI)](../dotnet/user-defined-operators-cpp-cli.md)

- [Konwersje zdefiniowane przez użytkownika (C++/CLI)](../dotnet/user-defined-conversions-cpp-cli.md)

- [Instrukcje: opakowywanie klasy natywnej do użycia w języku C#](../dotnet/how-to-wrap-native-class-for-use-by-csharp.md)

- [Klasy ogólne [C++/CLI]](../windows/generic-classes-cpp-cli.md)

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

### <a name="remarks"></a>Uwagi

Zobacz [klasy i struktury odwołania](../cppcx/ref-classes-and-structs-c-cx.md) i [klasy i struktury wartości](http://msdn.microsoft.com/library/windows/apps/hh699861.aspx).

### <a name="parameters"></a>Parametry

*base_type* (opcjonalnie)  
Typ podstawowy. A **klasy referencyjnej** lub **ref struct** może dziedziczyć z zero lub więcej interfejsów i zero lub jeden **ref** typów. A **klasę wartości** lub **struktury wartości** może dziedziczyć tylko z zero lub więcej interfejsów.

Kiedy Deklarujesz obiektu za pomocą **klasy referencyjnej** lub **ref struct** słów kluczowych, obiekt jest dostępny po dojścia do obiektu, czyli wskaźnik licznika odwołań do obiektu. Gdy zadeklarowana zmienna wykracza poza zakres, kompilator automatycznie usuwa obiekt źródłowy. Gdy obiekt jest używany jako parametr w wywołaniu lub jest przechowywana w zmiennej, dojścia do obiektu jest faktycznie przekazywane lub przechowywane.

Kiedy Deklarujesz obiektu za pomocą **klasę wartości** lub **struktury wartości** słów kluczowych, okres istnienia obiektów zadeklarowanych obiektu nie jest nadzorowane. Obiekt jest podobnie jak inne standard C++ klasy lub struktury.

### <a name="requirements"></a>Wymagania

— Opcja kompilatora: `/ZW`

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

### <a name="remarks"></a>Uwagi

W poniższej tabeli przedstawiono różnice w składni przedstawionej w **wszystkie środowiska wykonawcze** sekcji, które są specyficzne dla języka C + +/ interfejsu wiersza polecenia.

### <a name="parameters"></a>Parametry

*base_type* (opcjonalnie)  
Typ podstawowy. A **klasy referencyjnej** lub **ref struct** może dziedziczyć od zera lub jednego zarządzanego, interfejsy i zero lub jeden ref typów. A **klasę wartości** lub **struktury wartości** może dziedziczyć tylko z zero lub więcej interfejsów zarządzanych.

**Klasy referencyjnej** i **ref struct** słowa kluczowe poinformować kompilator, który ma zostać przydzielone na stercie klasy lub struktury. Gdy obiekt jest używany jako parametr w wywołaniu lub jest przechowywana w zmiennej, odwołanie do obiektu jest faktycznie przekazywane lub przechowywane.

**Klasę wartości** i **struktury wartości** słowa kluczowe informuje kompilator, że wartość przydzielone klasy lub struktury jest przekazywane do funkcji lub przechowywany w elementów członkowskich.

### <a name="requirements"></a>Wymagania

— Opcja kompilatora: `/clr`

## <a name="see-also"></a>Zobacz też

[Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)