---
title: 'Microsoft::wrl:: details Namespace | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: d71fe149-d804-4c6f-961d-43fe21ef8630
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f95eaa49db5e09bceaefafc16312250d823e5d5c
ms.sourcegitcommit: d1527eb2d50156bf923f2a32ec3af9efc7fc4304
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2018
ms.locfileid: "48250396"
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
|[ComPtrRef, klasa](../windows/comptrref-class.md)|Reprezentuje odwołanie do obiektu typu ComPtr\<T >.|
|[ComPtrRefBase, klasa](../windows/comptrrefbase-class.md)|Reprezentuje klasę bazową dla [comptrref —](../windows/comptrref-class.md) klasy.|
|[DontUseNewUseMake, klasa](../windows/dontusenewusemake-class.md)|Zapobiega za pomocą operatora **nowe** w `RuntimeClass`. W związku z tym, należy użyć [funkcji](../windows/make-function.md) zamiast tego.|
|[EventTargetArray, klasa](../windows/eventtargetarray-class.md)|Reprezentuje tablicę procedury obsługi zdarzeń.|
|[MakeAllocator, klasa](../windows/makeallocator-class.md)|Przydziela pamięć dla klasy aktywowalnej, z lub bez niej odwołanie tymczasowe wsparcia.|
|[ModuleBase, klasa](../windows/modulebase-class.md)|Reprezentuje klasę bazową [modułu](../windows/module-class.md) klasy.|
|[RemoveIUnknown, klasa](../windows/removeiunknown-class.md)|Tworzy typ, który jest odpowiednikiem `IUnknown`— na podstawie typu, ale ma niewirtualną `QueryInterface`, `AddRef`, i `Release` metody.|
|[Weakreference — klasa](../windows/weakreference-class.md)|Reprezentuje *słabe odwołanie* które mogą być używane z Windows Runtime lub Klasyczny model COM. Słabe odwołanie reprezentuje obiekt, który może być lub może być niedostępny.|

### <a name="structures"></a>Struktury

|Nazwa|Opis|
|----------|-----------------|
|[ArgTraits, struktura](../windows/argtraits-structure.md)|Deklaruje określonego delegata interfejsu i funkcji anonimowej składowej, która ma określoną liczbę parametrów.|
|[ArgTraitsHelper, struktura](../windows/argtraitshelper-structure.md)|Pomaga zdefiniować typowe cechy argumenty delegata.|
|[BoolStruct, struktura](../windows/boolstruct-structure.md)|Określa, czy `ComPtr` Zarządzanie okresem istnienia interfejsu. `BoolStruct` jest używana wewnętrznie przez [BoolType()](../windows/comptr-operator-microsoft-wrl-details-booltype-operator.md) operatora.|
|[CreatorMap, struktura](../windows/creatormap-structure.md)|Zawiera informacje o sposobie inicjowania, rejestrować i wyrejestrowywać obiektów.|
|[DerefHelper, struktura](../windows/derefhelper-structure.md)|Reprezentuje wskaźnik wyłuskiwany `T*` parametru szablonu.|
|[EnableIf, struktura](../windows/enableif-structure.md)|Definiuje element członkowski danych o typie określonym przez drugi parametr szablonu, jeśli pierwszy parametr szablonu, które daje w wyniku **true**.|
|[FactoryCache, struktura](../windows/factorycache-structure.md)|Zawiera lokalizację fabryki klas i wartość, która identyfikuje zarejestrowanych Windows Runtime lub COM obiektu klasy.|
|[ImplementsBase, struktura](../windows/implementsbase-structure.md)|Służy do sprawdzania typów parametrów szablonu w [Implements — struktura](../windows/implements-structure.md).|
|[ImplementsHelper, struktura](../windows/implementshelper-structure.md)|Pomaga wdrożyć [implementuje](../windows/implements-structure.md) struktury.|
|[InterfaceList, struktura](../windows/interfacelist-structure.md)|Użyty do utworzenia cyklicznego listę interfejsów.|
|[InterfaceListHelper, struktura](../windows/interfacelisthelper-structure.md)|Kompilacje `InterfaceList` typu przez rekursywnie stosowanie argumentów parametru określonego szablonu.|
|[InterfaceTraits, struktura](../windows/interfacetraits-structure.md)|Implementuje typowe cechy interfejsu.|
|[InvokeHelper, struktura](../windows/invokehelper-structure.md)|Udostępnia implementację `Invoke()` metody na podstawie określonej liczby i typów argumentów.|
|[IsBaseOfStrict, struktura](../windows/isbaseofstrict-structure.md)|Sprawdza, czy jest jeden typ podstawowy innego.|
|[IsSame, struktura](../windows/issame-structure.md)|Testy, czy jeden określony typ jest taki sam jak inny określony typ.|
|[Nil, struktura](../windows/nil-structure.md)|Służy do wskazania parametrem szablonu nieokreślony, opcjonalne.|
|[RemoveReference, struktura](../windows/removereference-structure.md)|Usuwa odwołanie lub odwołaniem rvalue cech od parametru szablonu określonej klasy.|
|[RuntimeClassBase, struktura](../windows/runtimeclassbase-structure.md)|Używane do wykrywania `RuntimeClass` w [wprowadzić](../windows/make-function.md) funkcji.|
|[RuntimeClassBaseT, struktura](../windows/runtimeclassbaset-structure.md)|Zapewnia metody pomocnika do `QueryInterface` operacji oraz pobieranie identyfikatorów interfejsu.|
|[VerifyInheritanceHelper, struktura](../windows/verifyinheritancehelper-structure.md)|Sprawdza, czy jeden interfejs jest tworzony na podstawie innego interfejsu.|
|[VerifyInterfaceHelper, struktura](../windows/verifyinterfacehelper-structure.md)|Sprawdza, czy interfejs określony przez parametr szablonu spełnia określone wymagania.|

### <a name="enumerations"></a>Wyliczenia

|Nazwa|Opis|
|----------|-----------------|
|[AsyncStatusInternal, wyliczenie](../windows/asyncstatusinternal-enumeration.md)|Określa mapowanie między wewnętrznego wyliczenia stanu operacji asynchronicznych i `Windows::Foundation::AsyncStatus` wyliczenia.|

### <a name="functions"></a>Funkcje

|Nazwa|Opis|
|----------|-----------------|
|[ActivationFactoryCallback, funkcja](../windows/activationfactorycallback-function.md)|Pobiera fabrykę aktywacji dla identyfikatora określonego aktywacji.|
|[Move, funkcja](../windows/move-function.md)|Przenosi określonego argumentu z jednej lokalizacji.|
|[RaiseException, funkcja](../windows/raiseexception-function.md)|Zgłasza wyjątek w wątku wywołującego.|
|[Swap — funkcja (WRL)](../windows/swap-function-wrl.md)|Zamienia wartości dwóch określonych argumentów.|
|[TerminateMap, funkcja](../windows/terminatemap-function.md)|Zamyka fabryki klas w określonym module.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** async.h client.h, corewrappers.h, event.h, ftm.h, implements.h, internal.h, module.h

**Namespace:** Microsoft::wrl:: details

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL, przestrzeń nazw](../windows/microsoft-wrl-namespace.md)<br/>
[Microsoft::WRL::Wrappers, przestrzeń nazw](../windows/microsoft-wrl-wrappers-namespace.md)