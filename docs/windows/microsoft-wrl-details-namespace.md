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
ms.openlocfilehash: 284d9393f7f967230fd3f7deb497a0e245d78dec
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
|[Comptrref — klasa](../windows/comptrref-class.md)|Reprezentuje odwołanie do obiektu typu comptr —\<T >.|  
|[Comptrrefbase — klasa](../windows/comptrrefbase-class.md)|Reprezentuje klasę podstawową dla [comptrref —](../windows/comptrref-class.md) klasy.|  
|[Dontusenewusemake — klasa](../windows/dontusenewusemake-class.md)|Zapobiega przy użyciu operatora `new` w `RuntimeClass`. W związku z tym, należy użyć [Make — funkcja](../windows/make-function.md) zamiast tego.|  
|[Eventtargetarray — klasa](../windows/eventtargetarray-class.md)|Reprezentuje tablicę procedury obsługi zdarzeń.|  
|[Makeallocator — klasa](../windows/makeallocator-class.md)|Przydziela pamięć dla klasy aktywowalnej, z lub bez obsługi słabe odwołanie.|  
|[Modulebase — klasa](../windows/modulebase-class.md)|Reprezentuje klasę podstawową [modułu](../windows/module-class.md) klasy.|  
|[Removeiunknown — klasa](../windows/removeiunknown-class.md)|Sprawia, że typ, który jest odpowiednikiem `IUnknown`— oparte na typie, ale ma niewirtualną `QueryInterface`, `AddRef`, i `Release` metody.|  
|[Weakreference — klasa](../windows/weakreference-class1.md)|Reprezentuje *słabe odwołanie* które mogą być używane z środowiska wykonawczego systemu Windows lub klasycznego modelu COM. Słabe odwołanie reprezentuje obiekt, który może lub nie mogą być niedostępne.|  
  
### <a name="structures"></a>Struktury  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Argtraits — struktura](../windows/argtraits-structure.md)|Deklaruje delegata określony interfejs i funkcja anonimowego elementu członkowskiego, która ma określoną liczbę parametrów.|  
|[Argtraitshelper — struktura](../windows/argtraitshelper-structure.md)|Pomaga zdefiniować wspólne cechy argumentów delegata.|  
|[Boolstruct — struktura](../windows/boolstruct-structure.md)|Określa, czy comptr — Zarządzanie okres istnienia obiektu interfejsu. Boolstruct — jest używana wewnętrznie przez [BoolType()](../windows/comptr-operator-microsoft-wrl-details-booltype-operator.md) operatora.|  
|[Creatormap — struktura](../windows/creatormap-structure.md)|Zawiera informacje o sposobie inicjowania, rejestrowanie i wyrejestrowywanie obiektów.|  
|[Derefhelper — struktura](../windows/derefhelper-structure.md)|Reprezentuje wyłuskiwany wskaźnik do `T*` parametru szablonu.|  
|[Enableif — struktura](../windows/enableif-structure.md)|Definiuje element członkowski danych o typie określonym drugi parametr szablonu, jeśli pierwszy parametr szablonu daje w wyniku `true`.|  
|[Factorycache — struktura](../windows/factorycache-structure.md)|Zawiera lokalizację fabrykę klas i wartość, która identyfikuje zarejestrowanego obiektu klasy środowiska wykonawczego systemu Windows lub COM.|  
|[Implementsbase — struktura](../windows/implementsbase-structure.md)|Służy do sprawdzania typów parametrów szablonu w [Implements — struktura](../windows/implements-structure.md).|  
|[Implementshelper — struktura](../windows/implementshelper-structure.md)|Ułatwia wdrożenie [implementuje](../windows/implements-structure.md) struktury.|  
|[Interfacelist — struktura](../windows/interfacelist-structure.md)|Pozwala utworzyć listę cykliczne interfejsów.|  
|[Interfacelisthelper — struktura](../windows/interfacelisthelper-structure.md)|Tworzy `InterfaceList` typu przez rekursywnie stosowania argumentów parametru określonego szablonu.|  
|[Interfacetraits — struktura](../windows/interfacetraits-structure.md)|Wspólne cechy zawiera implementację interfejsu.|  
|[Invokehelper — struktura](../windows/invokehelper-structure.md)|Udostępnia implementację metody Invoke() na podstawie określonej liczby i typy argumentów.|  
|[Isbaseofstrict — struktura](../windows/isbaseofstrict-structure.md)|Sprawdza, czy jest jeden typ podstawowy innego.|  
|[Issame — struktura](../windows/issame-structure.md)|Testy czy określić jeden typ jest taki sam jak inny określony typ.|  
|[Nil — struktura](../windows/nil-structure.md)|Służy do wskazania parametr szablonu nieokreślony, opcjonalne.|  
|[Removereference — struktura](../windows/removereference-structure.md)|Usuwa odwołanie lub odwołanie do r-wartości cechy z parametru szablonu określonej klasy.|  
|[Runtimeclassbase — struktura](../windows/runtimeclassbase-structure.md)|Używane do wykrywania `RuntimeClass` w [upewnij](../windows/make-function.md) funkcji.|  
|[Runtimeclassbaset — struktura](../windows/runtimeclassbaset-structure.md)|Udostępnia metody pomocnicze do `QueryInterface` operacje i pobieranie identyfikatorów interfejsu.|  
|[Verifyinheritancehelper — struktura](../windows/verifyinheritancehelper-structure.md)|Sprawdza, czy jeden interfejs pochodzi z innego interfejsu.|  
|[Verifyinterfacehelper — struktura](../windows/verifyinterfacehelper-structure.md)|Sprawdza, czy interfejs określonej przez parametr szablonu spełnia określone wymagania.|  
  
### <a name="enumerations"></a>Wyliczenia  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Asyncstatusinternal — wyliczenie](../windows/asyncstatusinternal-enumeration.md)|Określa mapowanie między wewnętrzny wyliczenia stanu operacji asynchronicznych i **Windows::Foundation::AsyncStatus** wyliczenia.|  
  
### <a name="functions"></a>Funkcje  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Activationfactorycallback — funkcja](../windows/activationfactorycallback-function.md)|Pobiera fabryki aktywacji dla aktywacji określonego identyfikatora.|  
|[MOVE — funkcja](../windows/move-function.md)|Przenosi określony argument z jednej lokalizacji.|  
|[Raiseexception — funkcja](../windows/raiseexception-function.md)|Zgłasza wyjątek w wątku wywołującym.|  
|[Swap — funkcja (Biblioteka szablonów języka C++ środowiska wykonawczego systemu Windows)](../windows/swap-function-windows-runtime-cpp-template-library.md)|Zamienia wartości dwóch określonych argumentów.|  
|[Terminatemap — funkcja](../windows/terminatemap-function.md)|Zamyka fabryki klas w określonym module.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** async.h, client.h, corewrappers.h, event.h, ftm.h, implements.h, internal.h, module.h  
  
 **Namespace:** Microsoft::wrl:: details —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::wrl — Namespace](../windows/microsoft-wrl-namespace.md)   
 [Microsoft::wrl:: wrappers — Namespace](../windows/microsoft-wrl-wrappers-namespace.md)