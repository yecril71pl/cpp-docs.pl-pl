---
title: Microsoft::WRL::Details — Przestrzeń nazw
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: d71fe149-d804-4c6f-961d-43fe21ef8630
ms.openlocfilehash: 50208242d77d7b54951bcb44608f1a20b5147efc
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223476"
---
# <a name="microsoftwrldetails-namespace"></a>Microsoft::WRL::Details — Przestrzeń nazw

Obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
namespace Microsoft::WRL::Details;
```

## <a name="members"></a>Elementy członkowskie

### <a name="classes"></a>Klasy

|Nazwa|Opis|
|----------|-----------------|
|[Klasa ComPtrRef](comptrref-class.md)|Reprezentuje odwołanie do obiektu typu ComPtr \<T> .|
|[Klasa ComPtrRefBase](comptrrefbase-class.md)|Reprezentuje klasę bazową dla klasy [ComPtrRef](comptrref-class.md) .|
|[Klasa DontUseNewUseMake](dontusenewusemake-class.md)|Uniemożliwia używanie operatora `new` w `RuntimeClass` . W związku z tym należy zamiast tego użyć [funkcji Make](make-function.md) .|
|[Klasa EventTargetArray](eventtargetarray-class.md)|Reprezentuje tablicę obsługi zdarzeń.|
|[Klasa MakeAllocator](makeallocator-class.md)|Przydziela pamięć dla klasy aktywowalnej z niesłabym wsparciem referencyjnym lub bez niego.|
|[Klasa ModuleBase](modulebase-class.md)|Reprezentuje klasę bazową klas [modułów](module-class.md) .|
|[Klasa RemoveIUnknown](removeiunknown-class.md)|Tworzy typ, który jest odpowiednikiem `IUnknown` typu opartego na typie, ale ma `QueryInterface` metody niewirtualne `AddRef` i i `Release` .|
|[Klasa WeakReference](weakreference-class.md)|Reprezentuje *słabe odwołanie* , które może być używane z środowisko wykonawcze systemu Windows lub klasycznego modelu com. Słabe odwołanie reprezentuje obiekt, który może lub nie jest dostępny.|

### <a name="structures"></a>Struktury

|Nazwa|Opis|
|----------|-----------------|
|[ArgTraits, struktura](argtraits-structure.md)|Deklaruje określony interfejs delegata i anonimową funkcję członkowską, która ma określoną liczbę parametrów.|
|[ArgTraitsHelper — Struktura](argtraitshelper-structure.md)|Ułatwia definiowanie typowych cech argumentów delegatów.|
|[BoolStruct, struktura](boolstruct-structure.md)|Określa, czy `ComPtr` zarządza okres istnienia obiektu w interfejsie. `BoolStruct`jest używany wewnętrznie przez operator [BoolType ()](comptr-class.md#operator-microsoft-wrl-details-booltype) .|
|[CreatorMap — Struktura](creatormap-structure.md)|Zawiera informacje o sposobach inicjowania, rejestrowania i wyrejestrowywania obiektów.|
|[DerefHelper, struktura](derefhelper-structure.md)|Reprezentuje wskaźnik odwołujący się do `T*` parametru szablonu.|
|[EnableIf, struktura](enableif-structure.md)|Definiuje element członkowski danych typu określonego przez drugi parametr szablonu, jeśli pierwszy parametr szablonu daje w wyniku **`true`** .|
|[FactoryCache — Struktura](factorycache-structure.md)|Zawiera lokalizację fabryki klasy i wartość, która identyfikuje zarejestrowany środowisko wykonawcze systemu Windows lub obiekt klasy COM.|
|[ImplementsBase, struktura](implementsbase-structure.md)|Służy do sprawdzania poprawności typów parametrów szablonu w [strukturze implementującej](implements-structure.md).|
|[ImplementsHelper — Struktura](implementshelper-structure.md)|Pomaga zaimplementować strukturę [implementującą](implements-structure.md) .|
|[InterfaceList — Struktura](interfacelist-structure.md)|Służy do tworzenia cyklicznej listy interfejsów.|
|[InterfaceListHelper — Struktura](interfacelisthelper-structure.md)|Kompiluje `InterfaceList` Typ przez cykliczne stosowanie określonych argumentów parametrów szablonu.|
|[InterfaceTraits — Struktura](interfacetraits-structure.md)|Implementuje typowe cechy interfejsu.|
|[InvokeHelper, struktura](invokehelper-structure.md)|Zapewnia implementację `Invoke()` metody w oparciu o określoną liczbę i typ argumentów.|
|[IsBaseOfStrict — Struktura](isbaseofstrict-structure.md)|Testuje, czy jeden typ jest podstawą innego.|
|[IsSame — Struktura](issame-structure.md)|Testuje, czy jeden określony typ jest taki sam jak inny określony typ.|
|[Nil — Struktura](nil-structure.md)|Służy do wskazywania nieokreślonego, opcjonalnego parametru szablonu.|
|[RemoveReference, struktura](removereference-structure.md)|Przypasaj cechy Reference lub rvalue z określonego parametru szablonu klasy.|
|[RuntimeClassBase — Struktura](runtimeclassbase-structure.md)|Używany do wykrywania `RuntimeClass` w funkcji [Make](make-function.md) .|
|[RuntimeClassBaseT, struktura](runtimeclassbaset-structure.md)|Dostarcza metody pomocnika do `QueryInterface` operacji i uzyskiwania identyfikatorów interfejsów.|
|[VerifyInheritanceHelper — Struktura](verifyinheritancehelper-structure.md)|Testuje, czy jeden interfejs pochodzi od innego interfejsu.|
|[VerifyInterfaceHelper, struktura](verifyinterfacehelper-structure.md)|Sprawdza, czy interfejs określony przez parametr szablonu spełnia określone wymagania.|

### <a name="enumerations"></a>Wyliczenia

|Nazwa|Opis|
|----------|-----------------|
|[AsyncStatusInternal — Wyliczenie](asyncstatusinternal-enumeration.md)|Określa mapowanie między wyliczeniami wewnętrznymi dla stanu operacji asynchronicznych i `Windows::Foundation::AsyncStatus` wyliczenia.|

### <a name="functions"></a>Funkcje

|Nazwa|Opis|
|----------|-----------------|
|[ActivationFactoryCallback —, funkcja](activationfactorycallback-function.md)|Pobiera fabrykę aktywacji dla określonego identyfikatora aktywacji.|
|[Move — funkcja](move-function.md)|Przenosi określony argument z jednej lokalizacji do innej.|
|[Funkcja podnosiexception](raiseexception-function.md)|Wywołuje wyjątek w wątku wywołującym.|
|[Swap — Funkcja (WRL)](swap-function-wrl.md)|Wymienia wartości dwóch określonych argumentów.|
|[TerminateMap —, funkcja](terminatemap-function.md)|Zamyka fabryki klas w określonym module.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** Async. h, Client. h, corewrappers. h, Event. h, FTM. h, implementuje. h, Internal. h, module. h

**Przestrzeń nazw:** Microsoft:: WRL::D etails

## <a name="see-also"></a>Zobacz też

[Microsoft:: WRL, przestrzeń nazw](microsoft-wrl-namespace.md)<br/>
[Microsoft:: WRL:: Otoke — przestrzeń nazw](microsoft-wrl-wrappers-namespace.md)
