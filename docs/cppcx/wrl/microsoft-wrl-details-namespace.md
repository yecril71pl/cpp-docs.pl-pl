---
title: Microsoft::WRL::Details — Przestrzeń nazw
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: d71fe149-d804-4c6f-961d-43fe21ef8630
ms.openlocfilehash: fce6e620600164e73d3708d98d8a7fa979e8ab42
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59027484"
---
# <a name="microsoftwrldetails-namespace"></a>Microsoft::WRL::Details — Przestrzeń nazw

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
namespace Microsoft::WRL::Details;
```

## <a name="members"></a>Elementy członkowskie

### <a name="classes"></a>Klasy

|Nazwa|Opis|
|----------|-----------------|
|[ComPtrRef — Klasa](comptrref-class.md)|Reprezentuje odwołanie do obiektu typu ComPtr\<T >.|
|[ComPtrRefBase — Klasa](comptrrefbase-class.md)|Reprezentuje klasę bazową dla [comptrref —](comptrref-class.md) klasy.|
|[DontUseNewUseMake — Klasa](dontusenewusemake-class.md)|Zapobiega za pomocą operatora `new` w `RuntimeClass`. W związku z tym, należy użyć [funkcji](make-function.md) zamiast tego.|
|[EventTargetArray — Klasa](eventtargetarray-class.md)|Reprezentuje tablicę procedury obsługi zdarzeń.|
|[MakeAllocator — Klasa](makeallocator-class.md)|Przydziela pamięć dla klasy aktywowalnej, z lub bez niej odwołanie tymczasowe wsparcia.|
|[ModuleBase — Klasa](modulebase-class.md)|Reprezentuje klasę bazową [modułu](module-class.md) klasy.|
|[RemoveIUnknown — Klasa](removeiunknown-class.md)|Tworzy typ, który jest odpowiednikiem `IUnknown`— na podstawie typu, ale ma niewirtualną `QueryInterface`, `AddRef`, i `Release` metody.|
|[WeakReference — Klasa](weakreference-class.md)|Reprezentuje *słabe odwołanie* które mogą być używane z Windows Runtime lub Klasyczny model COM. Słabe odwołanie reprezentuje obiekt, który może być lub może być niedostępny.|

### <a name="structures"></a>Struktury

|Nazwa|Opis|
|----------|-----------------|
|[ArgTraits — Struktura](argtraits-structure.md)|Deklaruje określonego delegata interfejsu i funkcji anonimowej składowej, która ma określoną liczbę parametrów.|
|[ArgTraitsHelper — Struktura](argtraitshelper-structure.md)|Pomaga zdefiniować typowe cechy argumenty delegata.|
|[BoolStruct — Struktura](boolstruct-structure.md)|Określa, czy `ComPtr` Zarządzanie okresem istnienia interfejsu. `BoolStruct` jest używana wewnętrznie przez [BoolType()](comptr-class.md#operator-microsoft-wrl-details-booltype) operatora.|
|[CreatorMap — Struktura](creatormap-structure.md)|Zawiera informacje o sposobie inicjowania, rejestrować i wyrejestrowywać obiektów.|
|[DerefHelper — Struktura](derefhelper-structure.md)|Reprezentuje wskaźnik wyłuskiwany `T*` parametru szablonu.|
|[EnableIf — Struktura](enableif-structure.md)|Definiuje element członkowski danych o typie określonym przez drugi parametr szablonu, jeśli pierwszy parametr szablonu, które daje w wyniku `true`.|
|[FactoryCache — Struktura](factorycache-structure.md)|Zawiera lokalizację fabryki klas i wartość, która identyfikuje zarejestrowanych Windows Runtime lub COM obiektu klasy.|
|[ImplementsBase — Struktura](implementsbase-structure.md)|Służy do sprawdzania typów parametrów szablonu w [Implements — struktura](implements-structure.md).|
|[ImplementsHelper — Struktura](implementshelper-structure.md)|Pomaga wdrożyć [implementuje](implements-structure.md) struktury.|
|[InterfaceList — Struktura](interfacelist-structure.md)|Użyty do utworzenia cyklicznego listę interfejsów.|
|[InterfaceListHelper — Struktura](interfacelisthelper-structure.md)|Kompilacje `InterfaceList` typu przez rekursywnie stosowanie argumentów parametru określonego szablonu.|
|[InterfaceTraits — Struktura](interfacetraits-structure.md)|Implementuje typowe cechy interfejsu.|
|[InvokeHelper — Struktura](invokehelper-structure.md)|Udostępnia implementację `Invoke()` metody na podstawie określonej liczby i typów argumentów.|
|[IsBaseOfStrict — Struktura](isbaseofstrict-structure.md)|Sprawdza, czy jest jeden typ podstawowy innego.|
|[IsSame — Struktura](issame-structure.md)|Testy, czy jeden określony typ jest taki sam jak inny określony typ.|
|[Nil — Struktura](nil-structure.md)|Służy do wskazania parametrem szablonu nieokreślony, opcjonalne.|
|[RemoveReference — Struktura](removereference-structure.md)|Usuwa odwołanie lub odwołaniem rvalue cech od parametru szablonu określonej klasy.|
|[RuntimeClassBase — Struktura](runtimeclassbase-structure.md)|Używane do wykrywania `RuntimeClass` w [wprowadzić](make-function.md) funkcji.|
|[RuntimeClassBaseT — Struktura](runtimeclassbaset-structure.md)|Zapewnia metody pomocnika do `QueryInterface` operacji oraz pobieranie identyfikatorów interfejsu.|
|[VerifyInheritanceHelper — Struktura](verifyinheritancehelper-structure.md)|Sprawdza, czy jeden interfejs jest tworzony na podstawie innego interfejsu.|
|[VerifyInterfaceHelper — Struktura](verifyinterfacehelper-structure.md)|Sprawdza, czy interfejs określony przez parametr szablonu spełnia określone wymagania.|

### <a name="enumerations"></a>Wyliczenia

|Nazwa|Opis|
|----------|-----------------|
|[AsyncStatusInternal — Wyliczenie](asyncstatusinternal-enumeration.md)|Określa mapowanie między wewnętrznego wyliczenia stanu operacji asynchronicznych i `Windows::Foundation::AsyncStatus` wyliczenia.|

### <a name="functions"></a>Funkcje

|Nazwa|Opis|
|----------|-----------------|
|[ActivationFactoryCallback — Funkcja](activationfactorycallback-function.md)|Pobiera fabrykę aktywacji dla identyfikatora określonego aktywacji.|
|[Move — Funkcja](move-function.md)|Przenosi określonego argumentu z jednej lokalizacji.|
|[RaiseException — Funkcja](raiseexception-function.md)|Zgłasza wyjątek w wątku wywołującego.|
|[Swap — funkcja (WRL)](swap-function-wrl.md)|Zamienia wartości dwóch określonych argumentów.|
|[TerminateMap — Funkcja](terminatemap-function.md)|Zamyka fabryki klas w określonym module.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** async.h client.h, corewrappers.h, event.h, ftm.h, implements.h, internal.h, module.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>Zobacz także

[Microsoft::WRL — Przestrzeń nazw](microsoft-wrl-namespace.md)<br/>
[Microsoft::WRL::Wrappers — Przestrzeń nazw](microsoft-wrl-wrappers-namespace.md)