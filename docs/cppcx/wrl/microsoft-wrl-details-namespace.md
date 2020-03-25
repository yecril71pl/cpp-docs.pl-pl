---
title: Microsoft::WRL::Details — Przestrzeń nazw
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: d71fe149-d804-4c6f-961d-43fe21ef8630
ms.openlocfilehash: 4e8d2e5a2c7e6655674c4e965cd7222d930dff9a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213788"
---
# <a name="microsoftwrldetails-namespace"></a>Microsoft::WRL::Details — Przestrzeń nazw

Obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
namespace Microsoft::WRL::Details;
```

## <a name="members"></a>Members

### <a name="classes"></a>Klasy

|Name (Nazwa)|Opis|
|----------|-----------------|
|[ComPtrRef, klasa](comptrref-class.md)|Reprezentuje odwołanie do obiektu typu ComPtr\<T >.|
|[ComPtrRefBase, klasa](comptrrefbase-class.md)|Reprezentuje klasę bazową dla klasy [ComPtrRef](comptrref-class.md) .|
|[DontUseNewUseMake, klasa](dontusenewusemake-class.md)|Uniemożliwia używanie operatora `new` w `RuntimeClass`. W związku z tym należy zamiast tego użyć [funkcji Make](make-function.md) .|
|[EventTargetArray, klasa](eventtargetarray-class.md)|Reprezentuje tablicę obsługi zdarzeń.|
|[MakeAllocator, klasa](makeallocator-class.md)|Przydziela pamięć dla klasy aktywowalnej z niesłabym wsparciem referencyjnym lub bez niego.|
|[ModuleBase, klasa](modulebase-class.md)|Reprezentuje klasę bazową klas [modułów](module-class.md) .|
|[RemoveIUnknown, klasa](removeiunknown-class.md)|Tworzy typ, który jest odpowiednikiem typu `IUnknown`, ale ma niewirtualne metody `QueryInterface`, `AddRef`i `Release`.|
|[WeakReference — Klasa](weakreference-class.md)|Reprezentuje *słabe odwołanie* , które może być używane z środowisko wykonawcze systemu Windows lub klasycznego modelu com. Słabe odwołanie reprezentuje obiekt, który może lub nie jest dostępny.|

### <a name="structures"></a>Struktury

|Name (Nazwa)|Opis|
|----------|-----------------|
|[ArgTraits, struktura](argtraits-structure.md)|Deklaruje określony interfejs delegata i anonimową funkcję członkowską, która ma określoną liczbę parametrów.|
|[ArgTraitsHelper, struktura](argtraitshelper-structure.md)|Ułatwia definiowanie typowych cech argumentów delegatów.|
|[BoolStruct, struktura](boolstruct-structure.md)|Określa, czy `ComPtr` zarządza okresem istnienia obiektu w interfejsie. `BoolStruct` jest używany wewnętrznie przez operator [BoolType ()](comptr-class.md#operator-microsoft-wrl-details-booltype) .|
|[CreatorMap, struktura](creatormap-structure.md)|Zawiera informacje o sposobach inicjowania, rejestrowania i wyrejestrowywania obiektów.|
|[DerefHelper, struktura](derefhelper-structure.md)|Reprezentuje wskaźnik odwołujący do parametru szablonu `T*`.|
|[EnableIf, struktura](enableif-structure.md)|Definiuje element członkowski danych typu określonego przez drugi parametr szablonu, jeśli pierwszy parametr szablonu szacuje się `true`.|
|[FactoryCache, struktura](factorycache-structure.md)|Zawiera lokalizację fabryki klasy i wartość, która identyfikuje zarejestrowany środowisko wykonawcze systemu Windows lub obiekt klasy COM.|
|[ImplementsBase, struktura](implementsbase-structure.md)|Służy do sprawdzania poprawności typów parametrów szablonu w [strukturze implementującej](implements-structure.md).|
|[ImplementsHelper, struktura](implementshelper-structure.md)|Pomaga zaimplementować strukturę [implementującą](implements-structure.md) .|
|[InterfaceList, struktura](interfacelist-structure.md)|Służy do tworzenia cyklicznej listy interfejsów.|
|[InterfaceListHelper, struktura](interfacelisthelper-structure.md)|Kompiluje typ `InterfaceList` przez cykliczne stosowanie określonych argumentów parametrów szablonu.|
|[InterfaceTraits, struktura](interfacetraits-structure.md)|Implementuje typowe cechy interfejsu.|
|[InvokeHelper, struktura](invokehelper-structure.md)|Zapewnia implementację metody `Invoke()` w oparciu o określoną liczbę i typ argumentów.|
|[IsBaseOfStrict, struktura](isbaseofstrict-structure.md)|Testuje, czy jeden typ jest podstawą innego.|
|[IsSame, struktura](issame-structure.md)|Testuje, czy jeden określony typ jest taki sam jak inny określony typ.|
|[Nil, struktura](nil-structure.md)|Służy do wskazywania nieokreślonego, opcjonalnego parametru szablonu.|
|[RemoveReference, struktura](removereference-structure.md)|Przypasaj cechy Reference lub rvalue z określonego parametru szablonu klasy.|
|[RuntimeClassBase, struktura](runtimeclassbase-structure.md)|Służy do wykrywania `RuntimeClass` w funkcji [Make](make-function.md) .|
|[RuntimeClassBaseT, struktura](runtimeclassbaset-structure.md)|Dostarcza metody pomocnika dla operacji `QueryInterface` i uzyskiwania identyfikatorów interfejsów.|
|[VerifyInheritanceHelper, struktura](verifyinheritancehelper-structure.md)|Testuje, czy jeden interfejs pochodzi od innego interfejsu.|
|[VerifyInterfaceHelper, struktura](verifyinterfacehelper-structure.md)|Sprawdza, czy interfejs określony przez parametr szablonu spełnia określone wymagania.|

### <a name="enumerations"></a>Wyliczenia

|Name (Nazwa)|Opis|
|----------|-----------------|
|[AsyncStatusInternal, wyliczenie](asyncstatusinternal-enumeration.md)|Określa mapowanie między wyliczeniem wewnętrznym dla stanu operacji asynchronicznych i wyliczeniem `Windows::Foundation::AsyncStatus`.|

### <a name="functions"></a>Funkcje

|Name (Nazwa)|Opis|
|----------|-----------------|
|[ActivationFactoryCallback, funkcja](activationfactorycallback-function.md)|Pobiera fabrykę aktywacji dla określonego identyfikatora aktywacji.|
|[Move, funkcja](move-function.md)|Przenosi określony argument z jednej lokalizacji do innej.|
|[RaiseException, funkcja](raiseexception-function.md)|Wywołuje wyjątek w wątku wywołującym.|
|[Swap — Funkcja (WRL)](swap-function-wrl.md)|Wymienia wartości dwóch określonych argumentów.|
|[TerminateMap, funkcja](terminatemap-function.md)|Zamyka fabryki klas w określonym module.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** Async. h, Client. h, corewrappers. h, Event. h, FTM. h, implementuje. h, Internal. h, module. h

**Przestrzeń nazw:** Microsoft:: WRL::D etails

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL, przestrzeń nazw](microsoft-wrl-namespace.md)<br/>
[Microsoft::WRL::Wrappers, przestrzeń nazw](microsoft-wrl-wrappers-namespace.md)
