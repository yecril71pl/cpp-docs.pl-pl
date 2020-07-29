---
title: ref class and ref struct (C++/CLI i C++/CX)
ms.date: 05/30/2019
ms.topic: reference
f1_keywords:
- ref class
- value class
- ref struct
- value struct
helpviewer_keywords:
- ref class keyword [C++]
- value class keyword [C++]
- value struct keyword [C++]
- ref struct keyword [C++]
ms.assetid: 5c360764-b229-49c6-9357-66213afbc372
ms.openlocfilehash: 42742d8fadad78702a665e5c53119f022bc00971
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228729"
---
# <a name="ref-class-and-ref-struct--ccli-and-ccx"></a>ref class and ref struct (C++/CLI i C++/CX)

Rozszerzenia **klasy ref** lub **ref struct** deklarują klasę lub strukturę, której *okres istnienia obiektu* jest zarządzany automatycznie. Gdy obiekt nie jest już dostępny lub wykracza poza zakres, pamięć zostanie wydzielona.

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
Obowiązkowe Dostępność klasy lub struktury poza zestawem. Możliwe wartości to **`public`** i **`private`** ( **`private`** jest to wartość domyślna). Zagnieżdżone klasy lub struktury nie mogą mieć specyfikatora *class_access* .

*Nazwij*<br/>
Nazwa klasy lub struktury.

*modyfikator*<br/>
Obowiązkowe [abstrakcyjne](abstract-cpp-component-extensions.md) i [zapieczętowane](sealed-cpp-component-extensions.md) są prawidłowymi modyfikatorami.

*inherit_access*<br/>
Obowiązkowe Dostępność *base_type*. Jedyna dozwolona dostępność to **`public`** (wartość **`public`** domyślna).

*base_type*<br/>
Obowiązkowe Typ podstawowy. Jednak typ wartości nie może działać jako typ podstawowy.

Aby uzyskać więcej informacji, zobacz opisy dotyczące języka dla tego parametru w sekcjach środowisko wykonawcze systemu Windows i środowiska uruchomieniowego języka wspólnego.

### <a name="remarks"></a>Uwagi

Domyślna dostępność elementu członkowskiego dla obiektu zadeklarowanego za pomocą klasy **ref** lub **klasy wartości** to **`private`** . A domyślną dostępnością elementu członkowskiego obiektu zadeklarowanego za pomocą **struktury ref** lub **struktury wartości** jest **`public`** .

Gdy typ referencyjny dziedziczy z innego typu odwołania, funkcje wirtualne w klasie bazowej muszą jawnie zostać zastąpione (z [zastąpieniem](override-cpp-component-extensions.md)) lub ukryty (z [nowym miejscem w tabeli metod wirtualnych)](new-new-slot-in-vtable-cpp-component-extensions.md)). Funkcje klasy pochodnej muszą być również jawnie oznaczone jako **`virtual`** .

Aby wykryć w czasie kompilacji, niezależnie od tego, czy typ jest **klasą referencyjną** , czy **strukturą ref**, czy **klasą wartości** lub **strukturą wartości**, użyj `__is_ref_class (type)` , `__is_value_class (type)` , lub `__is_simple_value_class (type)` . Aby uzyskać więcej informacji, zobacz [Obsługa kompilatora dla cech typu](compiler-support-for-type-traits-cpp-component-extensions.md).

Aby uzyskać więcej informacji na temat klas i struktur, zobacz

- [Tworzenie wystąpień klas i struktur](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md)

- [Semantyka stosu języka C++ dla typów referencyjnych](../dotnet/cpp-stack-semantics-for-reference-types.md)

- [Klasy, struktury i związki](../cpp/classes-and-structs-cpp.md)

- [Destruktory i finalizatory w instrukcje: Definiowanie i korzystanie z klas i struktur (C++/CLI)](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)

- [Operatory zdefiniowane przez użytkownika (C++/CLI)](../dotnet/user-defined-operators-cpp-cli.md)

- [Konwersje zdefiniowane przez użytkownika (C++/CLI)](../dotnet/user-defined-conversions-cpp-cli.md)

- [Instrukcje: Zawijanie klasy natywnej do użycia przez C #](../dotnet/how-to-wrap-native-class-for-use-by-csharp.md)

- [Klasy ogólne [C++/CLI]](generic-classes-cpp-cli.md)

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

### <a name="remarks"></a>Uwagi

Zobacz [klasy referencyjne i struktury](../cppcx/ref-classes-and-structs-c-cx.md) oraz [klasy wartości i struktury](../cppcx/value-classes-and-structs-c-cx.md).

### <a name="parameters"></a>Parametry

*base_type*<br/>
Obowiązkowe Typ podstawowy. **Klasa ref** lub **ref struct** mogą dziedziczyć z zero lub więcej interfejsów i zero lub jeden typ **ref** . **Klasa wartości** lub **Struktura wartości** może dziedziczyć tylko po zero lub większej liczbie interfejsów.

Gdy deklarujesz obiekt za pomocą słowa kluczowego **ref** lub **ref struct** , uzyskuje dostęp do obiektu za pomocą dojścia do obiektu; oznacza to, że wskaźnik licznika odwołania do obiektu. Gdy zadeklarowana zmienna wykracza poza zakres, kompilator automatycznie usuwa obiekt źródłowy. Gdy obiekt jest używany jako parametr w wywołaniu lub jest przechowywany w zmiennej, dojście do obiektu jest faktycznie przekazywanie lub przechowywane.

Podczas deklarowania obiektu za pomocą **klasy wartości** lub słów kluczowych **struktury wartości** , okres istnienia obiektu zadeklarowanego obiektu nie jest nadzorowany. Obiekt jest podobny do żadnej innej standardowej klasy C++ lub struktury.

### <a name="requirements"></a>Wymagania

Opcja kompilatora:`/ZW`

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

### <a name="remarks"></a>Uwagi

W poniższej tabeli wymieniono różnice dotyczące składni pokazanej w sekcji **wszystkie środowiska uruchomieniowe** , które są specyficzne dla języka C++/CLI.

### <a name="parameters"></a>Parametry

*base_type*<br/>
Obowiązkowe Typ podstawowy. **Klasa ref** lub **ref struct** mogą dziedziczyć z zero lub więcej interfejsów zarządzanych i zero lub jeden typ ref. **Klasa wartości** lub **Struktura wartości** może dziedziczyć tylko po zerowym lub większym interfejsie zarządzanym.

Słowa kluczowe **ref** i **ref struct** , które informują kompilator, że Klasa lub struktura są przydzielane na stercie. Gdy obiekt jest używany jako parametr w wywołaniu lub jest przechowywany w zmiennej, odwołanie do obiektu jest faktycznie przekazywanie lub przechowywane.

Słowa kluczowe **klasy wartości** i **struktury wartości** instruują kompilator, że wartość przydzieloną klasy lub struktury jest przenoszona do funkcji lub przechowywanych w elementach członkowskich.

### <a name="requirements"></a>Wymagania

Opcja kompilatora:`/clr`

## <a name="see-also"></a>Zobacz także

[Rozszerzenia składników dla platform .NET i platformy UWP](component-extensions-for-runtime-platforms.md)
