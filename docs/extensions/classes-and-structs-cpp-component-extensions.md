---
title: Klasa ref i ref struct (C++sposób niezamierzony i C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- ref class keyword [C++]
- value class keyword [C++]
- value struct keyword [C++]
- ref struct keyword [C++]
ms.assetid: 5c360764-b229-49c6-9357-66213afbc372
ms.openlocfilehash: fcc50109ce521e005e32a8c19b13aabe2230989b
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59029734"
---
# <a name="ref-class-and-ref-struct--ccli-and-ccx"></a>Klasa ref i ref struct (C++sposób niezamierzony i C++/CX)

**Klasy referencyjnej** lub **ref struct** rozszerzenia zadeklarować klasy lub struktury którego *okres istnienia obiektu* są zarządzane automatycznie. Gdy obiekt nie jest już dostępny, lub wykracza poza zakres, pamięć jest zwalniana.

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

*class_access*<br/>
(Opcjonalnie) Dostępność klasy lub struktury spoza zestawu. Możliwe wartości to **publicznych** i **prywatnej** (**prywatnej** jest ustawieniem domyślnym). Zagnieżdżone klasy lub struktury nie mogą mieć *class_access* specyfikator.

*Nazwa*<br/>
Nazwa klasy lub struktury.

*modifier*<br/>
(Opcjonalnie) [abstrakcyjne](abstract-cpp-component-extensions.md) i [zapieczętowanego](sealed-cpp-component-extensions.md) są prawidłowe modyfikatorów.

*inherit_access*<br/>
(Opcjonalnie) Dostępność *base_type*. Tylko dozwolone ułatwień dostępu jest **publicznych** (**publicznych** jest ustawieniem domyślnym).

*base_type*<br/>
(Opcjonalnie) Typ podstawowy. Jednak typ wartościowy nie może działać jako typu podstawowego.

Aby uzyskać więcej informacji zobacz opisy specyficzny dla języka tego parametru w sekcjach środowiska uruchomieniowego Windows i środowisko uruchomieniowe języka wspólnego.

### <a name="remarks"></a>Uwagi

Wartość domyślna dostępu elementu członkowskiego obiektu zadeklarowane za pomocą **klasy referencyjnej** lub **klasę wartości** jest **prywatnej**. I ułatwienia dostępu członków domyślnego obiektu zadeklarowane za pomocą **ref struct** lub **struktury wartości** jest **publicznych**.

Gdy typ odwołania dziedziczy z innego typu odwołania, funkcje wirtualne w klasie bazowej jawnie musi zostać zastąpiona (przy użyciu [zastąpienia](override-cpp-component-extensions.md)) lub ukryte (przy użyciu [new (nowe gniazdo w vtable)](new-new-slot-in-vtable-cpp-component-extensions.md)). Funkcje klasy pochodnej musi również jawnie oznaczona jako **wirtualnego**.

Aby wykryć w czasie kompilacji, czy typ jest **klasy referencyjnej** lub **ref struct**, lub **klasę wartości** lub **struktury wartości**, użyj `__is_ref_class (type)`, `__is_value_class (type)`, lub `__is_simple_value_class (type)`. Aby uzyskać więcej informacji, zobacz [Obsługa cech typu w kompilatorze](compiler-support-for-type-traits-cpp-component-extensions.md).

Aby uzyskać więcej informacji na temat klas i struktur zobacz

- [Utworzenie wystąpienia klasy i struktury](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md)

- [Semantyka stosu języka C++ dla typów odwołań](../dotnet/cpp-stack-semantics-for-reference-types.md)

- [Klas, struktur i Unii](../cpp/classes-and-structs-cpp.md)

- [Destruktory i finalizatory w sposób: Definiowanie oraz stosowanie klas i struktur (C++sposób niezamierzony)](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)

- [Operatory zdefiniowane przez użytkownika (C++/CLI)](../dotnet/user-defined-operators-cpp-cli.md)

- [Konwersje zdefiniowane przez użytkownika (C++/CLI)](../dotnet/user-defined-conversions-cpp-cli.md)

- [Instrukcje: opakowywanie klasy natywnej do użycia w języku C#](../dotnet/how-to-wrap-native-class-for-use-by-csharp.md)

- [Klasy ogólne [C++/CLI]](generic-classes-cpp-cli.md)

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

### <a name="remarks"></a>Uwagi

Zobacz [klasy i struktury odwołania](../cppcx/ref-classes-and-structs-c-cx.md) i [klasy i struktury wartości](https://msdn.microsoft.com/library/windows/apps/hh699861.aspx).

### <a name="parameters"></a>Parametry

*base_type*<br/>
(Opcjonalnie) Typ podstawowy. A **klasy referencyjnej** lub **ref struct** może dziedziczyć z zero lub więcej interfejsów i zero lub jeden **ref** typów. A **klasę wartości** lub **struktury wartości** może dziedziczyć tylko z zero lub więcej interfejsów.

Kiedy Deklarujesz obiektu za pomocą **klasy referencyjnej** lub **ref struct** słów kluczowych, obiekt jest dostępny po dojścia do obiektu, czyli wskaźnik licznika odwołań do obiektu. Gdy zadeklarowana zmienna wykracza poza zakres, kompilator automatycznie usuwa obiekt źródłowy. Gdy obiekt jest używany jako parametr w wywołaniu lub jest przechowywana w zmiennej, dojścia do obiektu jest faktycznie przekazywane lub przechowywane.

Kiedy Deklarujesz obiektu za pomocą **klasę wartości** lub **struktury wartości** słów kluczowych, okres istnienia obiektów zadeklarowanych obiektu nie jest nadzorowane. Obiekt jest podobnie jak inne standard C++ klasy lub struktury.

### <a name="requirements"></a>Wymagania

— Opcja kompilatora: `/ZW`

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

### <a name="remarks"></a>Uwagi

W poniższej tabeli przedstawiono różnice w składni przedstawionej w **wszystkie środowiska wykonawcze** sekcji, które są specyficzne dla C++sposób niezamierzony.

### <a name="parameters"></a>Parametry

*base_type*<br/>
(Opcjonalnie) Typ podstawowy. A **klasy referencyjnej** lub **ref struct** może dziedziczyć od zera lub jednego zarządzanego, interfejsy i zero lub jeden ref typów. A **klasę wartości** lub **struktury wartości** może dziedziczyć tylko z zero lub więcej interfejsów zarządzanych.

**Klasy referencyjnej** i **ref struct** słowa kluczowe poinformować kompilator, który ma zostać przydzielone na stercie klasy lub struktury. Gdy obiekt jest używany jako parametr w wywołaniu lub jest przechowywana w zmiennej, odwołanie do obiektu jest faktycznie przekazywane lub przechowywane.

**Klasę wartości** i **struktury wartości** słowa kluczowe informuje kompilator, że wartość przydzielone klasy lub struktury jest przekazywane do funkcji lub przechowywany w elementów członkowskich.

### <a name="requirements"></a>Wymagania

— Opcja kompilatora: `/clr`

## <a name="see-also"></a>Zobacz także

[Rozszerzenia składników dla platformy .NET i platformy uniwersalnej systemu Windows](component-extensions-for-runtime-platforms.md)