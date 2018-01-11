---
title: "Microsoft::wrl:: details — Namespace | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
ms.assetid: d71fe149-d804-4c6f-961d-43fe21ef8630
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f005969908252602cb2fb4bdd73d3b55ae342a99
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="microsoftwrldetails-namespace"></a>Microsoft::WRL::Details — Przestrzeń nazw
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
namespace Microsoft::WRL::Details;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="classes"></a>Klasy  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[ComPtrRef, klasa](../windows/comptrref-class.md)|Reprezentuje odwołanie do obiektu typu comptr —\<T >.|  
|[ComPtrRefBase, klasa](../windows/comptrrefbase-class.md)|Reprezentuje klasę podstawową dla [comptrref —](../windows/comptrref-class.md) klasy.|  
|[DontUseNewUseMake, klasa](../windows/dontusenewusemake-class.md)|Zapobiega przy użyciu operatora `new` w `RuntimeClass`. W związku z tym, należy użyć [Make — funkcja](../windows/make-function.md) zamiast tego.|  
|[EventTargetArray, klasa](../windows/eventtargetarray-class.md)|Reprezentuje tablicę procedury obsługi zdarzeń.|  
|[MakeAllocator, klasa](../windows/makeallocator-class.md)|Przydziela pamięć dla klasy aktywowalnej, z lub bez obsługi słabe odwołanie.|  
|[ModuleBase, klasa](../windows/modulebase-class.md)|Reprezentuje klasę podstawową [modułu](../windows/module-class.md) klasy.|  
|[RemoveIUnknown, klasa](../windows/removeiunknown-class.md)|Sprawia, że typ, który jest odpowiednikiem `IUnknown`— oparte na typie, ale ma niewirtualną `QueryInterface`, `AddRef`, i `Release` metody.|  
|[Weakreference — klasa](../windows/weakreference-class1.md)|Reprezentuje *słabe odwołanie* które mogą być używane z środowiska wykonawczego systemu Windows lub klasycznego modelu COM. Słabe odwołanie reprezentuje obiekt, który może lub nie mogą być niedostępne.|  
  
### <a name="structures"></a>Struktury  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[ArgTraits, struktura](../windows/argtraits-structure.md)|Deklaruje delegata określony interfejs i funkcja anonimowego elementu członkowskiego, która ma określoną liczbę parametrów.|  
|[ArgTraitsHelper, struktura](../windows/argtraitshelper-structure.md)|Pomaga zdefiniować wspólne cechy argumentów delegata.|  
|[BoolStruct, struktura](../windows/boolstruct-structure.md)|Określa, czy comptr — Zarządzanie okres istnienia obiektu interfejsu. Boolstruct — jest używana wewnętrznie przez [BoolType()](../windows/comptr-operator-microsoft-wrl-details-booltype-operator.md) operatora.|  
|[CreatorMap, struktura](../windows/creatormap-structure.md)|Zawiera informacje o sposobie inicjowania, rejestrowanie i wyrejestrowywanie obiektów.|  
|[DerefHelper, struktura](../windows/derefhelper-structure.md)|Reprezentuje wyłuskiwany wskaźnik do `T*` parametru szablonu.|  
|[EnableIf, struktura](../windows/enableif-structure.md)|Definiuje element członkowski danych o typie określonym drugi parametr szablonu, jeśli pierwszy parametr szablonu daje w wyniku `true`.|  
|[FactoryCache, struktura](../windows/factorycache-structure.md)|Zawiera lokalizację fabrykę klas i wartość, która identyfikuje zarejestrowanego obiektu klasy środowiska wykonawczego systemu Windows lub COM.|  
|[ImplementsBase, struktura](../windows/implementsbase-structure.md)|Służy do sprawdzania typów parametrów szablonu w [Implements — struktura](../windows/implements-structure.md).|  
|[ImplementsHelper, struktura](../windows/implementshelper-structure.md)|Ułatwia wdrożenie [implementuje](../windows/implements-structure.md) struktury.|  
|[InterfaceList, struktura](../windows/interfacelist-structure.md)|Pozwala utworzyć listę cykliczne interfejsów.|  
|[InterfaceListHelper, struktura](../windows/interfacelisthelper-structure.md)|Tworzy `InterfaceList` typu przez rekursywnie stosowania argumentów parametru określonego szablonu.|  
|[InterfaceTraits, struktura](../windows/interfacetraits-structure.md)|Wspólne cechy zawiera implementację interfejsu.|  
|[InvokeHelper, struktura](../windows/invokehelper-structure.md)|Udostępnia implementację metody Invoke() na podstawie określonej liczby i typy argumentów.|  
|[IsBaseOfStrict, struktura](../windows/isbaseofstrict-structure.md)|Sprawdza, czy jest jeden typ podstawowy innego.|  
|[IsSame, struktura](../windows/issame-structure.md)|Testy czy określić jeden typ jest taki sam jak inny określony typ.|  
|[Nil, struktura](../windows/nil-structure.md)|Służy do wskazania parametr szablonu nieokreślony, opcjonalne.|  
|[RemoveReference, struktura](../windows/removereference-structure.md)|Usuwa odwołanie lub odwołanie do r-wartości cechy z parametru szablonu określonej klasy.|  
|[RuntimeClassBase, struktura](../windows/runtimeclassbase-structure.md)|Używane do wykrywania `RuntimeClass` w [upewnij](../windows/make-function.md) funkcji.|  
|[RuntimeClassBaseT, struktura](../windows/runtimeclassbaset-structure.md)|Udostępnia metody pomocnicze do `QueryInterface` operacje i pobieranie identyfikatorów interfejsu.|  
|[VerifyInheritanceHelper, struktura](../windows/verifyinheritancehelper-structure.md)|Sprawdza, czy jeden interfejs pochodzi z innego interfejsu.|  
|[VerifyInterfaceHelper, struktura](../windows/verifyinterfacehelper-structure.md)|Sprawdza, czy interfejs określonej przez parametr szablonu spełnia określone wymagania.|  
  
### <a name="enumerations"></a>Wyliczenia  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[AsyncStatusInternal, wyliczenie](../windows/asyncstatusinternal-enumeration.md)|Określa mapowanie między wewnętrzny wyliczenia stanu operacji asynchronicznych i **Windows::Foundation::AsyncStatus** wyliczenia.|  
  
### <a name="functions"></a>Funkcje  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[ActivationFactoryCallback, funkcja](../windows/activationfactorycallback-function.md)|Pobiera fabryki aktywacji dla aktywacji określonego identyfikatora.|  
|[Move, funkcja](../windows/move-function.md)|Przenosi określony argument z jednej lokalizacji.|  
|[RaiseException, funkcja](../windows/raiseexception-function.md)|Zgłasza wyjątek w wątku wywołującym.|  
|[Swap, funkcja (Biblioteka szablonów języka C++ środowiska uruchomieniowego systemu Windows)](../windows/swap-function-windows-runtime-cpp-template-library.md)|Zamienia wartości dwóch określonych argumentów.|  
|[TerminateMap, funkcja](../windows/terminatemap-function.md)|Zamyka fabryki klas w określonym module.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** async.h, client.h, corewrappers.h, event.h, ftm.h, implements.h, internal.h, module.h  
  
 **Namespace:** Microsoft::wrl:: details —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::wrl — Namespace](../windows/microsoft-wrl-namespace.md)   
 [Microsoft::WRL::Wrappers, przestrzeń nazw](../windows/microsoft-wrl-wrappers-namespace.md)