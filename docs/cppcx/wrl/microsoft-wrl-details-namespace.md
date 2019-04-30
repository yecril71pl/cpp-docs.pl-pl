---
title: Microsoft::WRL::Details — Przestrzeń nazw
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: d71fe149-d804-4c6f-961d-43fe21ef8630
ms.openlocfilehash: fce6e620600164e73d3708d98d8a7fa979e8ab42
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392040"
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
|[ComPtrRef, klasa](comptrref-class.md)|Reprezentuje odwołanie do obiektu typu ComPtr\<T >.|
|[ComPtrRefBase, klasa](comptrrefbase-class.md)|Reprezentuje klasę bazową dla [comptrref —](comptrref-class.md) klasy.|
|[DontUseNewUseMake, klasa](dontusenewusemake-class.md)|Zapobiega za pomocą operatora `new` w `RuntimeClass`. W związku z tym, należy użyć [funkcji](make-function.md) zamiast tego.|
|[EventTargetArray, klasa](eventtargetarray-class.md)|Reprezentuje tablicę procedury obsługi zdarzeń.|
|[MakeAllocator, klasa](makeallocator-class.md)|Przydziela pamięć dla klasy aktywowalnej, z lub bez niej odwołanie tymczasowe wsparcia.|
|[ModuleBase, klasa](modulebase-class.md)|Reprezentuje klasę bazową [modułu](module-class.md) klasy.|
|[RemoveIUnknown, klasa](removeiunknown-class.md)|Tworzy typ, który jest odpowiednikiem `IUnknown`— na podstawie typu, ale ma niewirtualną `QueryInterface`, `AddRef`, i `Release` metody.|
|[WeakReference — Klasa](weakreference-class.md)|Reprezentuje *słabe odwołanie* które mogą być używane z Windows Runtime lub Klasyczny model COM. Słabe odwołanie reprezentuje obiekt, który może być lub może być niedostępny.|

### <a name="structures"></a>Struktury

|Nazwa|Opis|
|----------|-----------------|
|[ArgTraits, struktura](argtraits-structure.md)|Deklaruje określonego delegata interfejsu i funkcji anonimowej składowej, która ma określoną liczbę parametrów.|
|[ArgTraitsHelper, struktura](argtraitshelper-structure.md)|Pomaga zdefiniować typowe cechy argumenty delegata.|
|[BoolStruct, struktura](boolstruct-structure.md)|Określa, czy `ComPtr` Zarządzanie okresem istnienia interfejsu. `BoolStruct` jest używana wewnętrznie przez [BoolType()](comptr-class.md#operator-microsoft-wrl-details-booltype) operatora.|
|[CreatorMap, struktura](creatormap-structure.md)|Zawiera informacje o sposobie inicjowania, rejestrować i wyrejestrowywać obiektów.|
|[DerefHelper, struktura](derefhelper-structure.md)|Reprezentuje wskaźnik wyłuskiwany `T*` parametru szablonu.|
|[EnableIf, struktura](enableif-structure.md)|Definiuje element członkowski danych o typie określonym przez drugi parametr szablonu, jeśli pierwszy parametr szablonu, które daje w wyniku `true`.|
|[FactoryCache, struktura](factorycache-structure.md)|Zawiera lokalizację fabryki klas i wartość, która identyfikuje zarejestrowanych Windows Runtime lub COM obiektu klasy.|
|[ImplementsBase, struktura](implementsbase-structure.md)|Służy do sprawdzania typów parametrów szablonu w [Implements — struktura](implements-structure.md).|
|[ImplementsHelper, struktura](implementshelper-structure.md)|Pomaga wdrożyć [implementuje](implements-structure.md) struktury.|
|[InterfaceList, struktura](interfacelist-structure.md)|Użyty do utworzenia cyklicznego listę interfejsów.|
|[InterfaceListHelper, struktura](interfacelisthelper-structure.md)|Kompilacje `InterfaceList` typu przez rekursywnie stosowanie argumentów parametru określonego szablonu.|
|[InterfaceTraits, struktura](interfacetraits-structure.md)|Implementuje typowe cechy interfejsu.|
|[InvokeHelper, struktura](invokehelper-structure.md)|Udostępnia implementację `Invoke()` metody na podstawie określonej liczby i typów argumentów.|
|[IsBaseOfStrict, struktura](isbaseofstrict-structure.md)|Sprawdza, czy jest jeden typ podstawowy innego.|
|[IsSame, struktura](issame-structure.md)|Testy, czy jeden określony typ jest taki sam jak inny określony typ.|
|[Nil, struktura](nil-structure.md)|Służy do wskazania parametrem szablonu nieokreślony, opcjonalne.|
|[RemoveReference, struktura](removereference-structure.md)|Usuwa odwołanie lub odwołaniem rvalue cech od parametru szablonu określonej klasy.|
|[RuntimeClassBase, struktura](runtimeclassbase-structure.md)|Używane do wykrywania `RuntimeClass` w [wprowadzić](make-function.md) funkcji.|
|[RuntimeClassBaseT, struktura](runtimeclassbaset-structure.md)|Zapewnia metody pomocnika do `QueryInterface` operacji oraz pobieranie identyfikatorów interfejsu.|
|[VerifyInheritanceHelper, struktura](verifyinheritancehelper-structure.md)|Sprawdza, czy jeden interfejs jest tworzony na podstawie innego interfejsu.|
|[VerifyInterfaceHelper, struktura](verifyinterfacehelper-structure.md)|Sprawdza, czy interfejs określony przez parametr szablonu spełnia określone wymagania.|

### <a name="enumerations"></a>Wyliczenia

|Nazwa|Opis|
|----------|-----------------|
|[AsyncStatusInternal, wyliczenie](asyncstatusinternal-enumeration.md)|Określa mapowanie między wewnętrznego wyliczenia stanu operacji asynchronicznych i `Windows::Foundation::AsyncStatus` wyliczenia.|

### <a name="functions"></a>Funkcje

|Nazwa|Opis|
|----------|-----------------|
|[ActivationFactoryCallback, funkcja](activationfactorycallback-function.md)|Pobiera fabrykę aktywacji dla identyfikatora określonego aktywacji.|
|[Move, funkcja](move-function.md)|Przenosi określonego argumentu z jednej lokalizacji.|
|[RaiseException, funkcja](raiseexception-function.md)|Zgłasza wyjątek w wątku wywołującego.|
|[Swap — Funkcja (WRL)](swap-function-wrl.md)|Zamienia wartości dwóch określonych argumentów.|
|[TerminateMap, funkcja](terminatemap-function.md)|Zamyka fabryki klas w określonym module.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** async.h client.h, corewrappers.h, event.h, ftm.h, implements.h, internal.h, module.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>Zobacz także

[Microsoft::WRL, przestrzeń nazw](microsoft-wrl-namespace.md)<br/>
[Microsoft::WRL::Wrappers, przestrzeń nazw](microsoft-wrl-wrappers-namespace.md)