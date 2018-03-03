---
title: "Kluczowe interfejsy API biblioteki WRL według kategorii | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
ms.assetid: 7367bacf-6b7c-4ecd-a0ce-a662db46fc66
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7ad38d1b24ca40b6209295f873bd44c54c3f6148
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="key-wrl-apis-by-category"></a>Kluczowe interfejsy API biblioteki WRL według kategorii
W poniższych tabelach przedstawiono podstawowe klasy, struktury, funkcjami i makrami Biblioteka szablonów C++ środowiska wykonawczego systemu Windows. Konstrukcje w pomocnika obszary nazw i klas są pomijane. Te listy rozszerzyć w dokumentacji interfejsu API, które są zorganizowane według przestrzeni nazw.  
  
### <a name="classes"></a>Klasy  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[ActivationFactory, klasa](../windows/activationfactory-class.md)|Umożliwia co najmniej jedną klasę do aktywacji przez środowisko wykonawcze systemu Windows.|  
|[AsyncBase, klasa](../windows/asyncbase-class.md)|Implementuje automatu stanów asynchroniczne środowiska wykonawczego systemu Windows.|  
|[ClassFactory, klasa](../windows/classfactory-class.md)|Implementuje podstawowych funkcji `IClassFactory` interfejsu.|  
|[ComPtr, klasa](../windows/comptr-class.md)|Tworzy *wskaźnika inteligentnego* typu, który reprezentuje interfejs określonej przez parametr szablonu. Comptr — automatycznie przechowuje licznika odwołań do podstawowej wskaźnika interfejsu i zwalnia interfejsu, gdy liczba odwołań do zera.|  
|[Event, klasa (Biblioteka szablonów języka C++ środowiska uruchomieniowego systemu Windows)](../windows/event-class-windows-runtime-cpp-template-library.md)|Reprezentuje zdarzenie.|  
|[EventSource, klasa](../windows/eventsource-class.md)|Reprezentuje zdarzenie. `EventSource`Funkcje Członkowskie dodawania, usuwania i wywołanie procedury obsługi zdarzeń.|  
|[FtmBase, klasa](../windows/ftmbase-class.md)|Reprezentuje obiekt opcja.|  
|[HandleT, klasa](../windows/handlet-class.md)|Reprezentuje uchwyt do obiektu.|  
|[HString, klasa](../windows/hstring-class.md)|Zapewnia obsługę manipulowanie HSTRING uchwytów.|  
|[HStringReference, klasa](../windows/hstringreference-class.md)|Reprezentuje wartość HSTRING utworzona na podstawie istniejących parametrów.|  
|[Klasa modułu](../windows/module-class.md)|Reprezentuje kolekcję obiektów pokrewnych.|  
|[Module::GenericReleaseNotifier, klasa](../windows/module-genericreleasenotifier-class.md)|Wywołuje program obsługi zdarzeń po zwolnieniu ostatni obiekt w bieżącego modułu. Program obsługi zdarzeń jest określona przez na lambda, obiekt lub wskaźnik do funkcji.|  
|[Module::MethodReleaseNotifier, klasa](../windows/module-methodreleasenotifier-class.md)|Wywołuje program obsługi zdarzeń po zwolnieniu ostatni obiekt w bieżącego modułu. Program obsługi zdarzeń jest określona przez obiekt i jego elementów członkowskich wskaźnika do metody.|  
|[Module::ReleaseNotifier, klasa](../windows/module-releasenotifier-class.md)|Wywołuje program obsługi zdarzeń po zwolnieniu ostatni obiekt w module.|  
|[RoInitializeWrapper, klasa](../windows/roinitializewrapper-class.md)|Inicjuje środowiska uruchomieniowego systemu Windows.|  
|[RuntimeClass, klasa](../windows/runtimeclass-class.md)|Reprezentuje wystąpień klasy, która dziedziczy określona liczba interfejsów i zapewnia określonego środowiska wykonawczego systemu Windows, klasycznego modelu COM i obsługa słabe odwołanie.|  
|[SimpleActivationFactory, klasa](../windows/simpleactivationfactory-class.md)|Udostępnia mechanizm podstawowych do utworzenia środowiska wykonawczego systemu Windows lub klasycznego modelu COM klasy podstawowej.|  
|[SimpleClassFactory, klasa](../windows/simpleclassfactory-class.md)|Udostępnia mechanizm podstawowych, aby utworzyć klasę podstawową.|  
|[WeakRef, klasa](../windows/weakref-class.md)|Reprezentuje *słabe odwołanie* które mogą być używane przez tylko środowiska uruchomieniowego systemu Windows, nie klasycznego modelu COM. Słabe odwołanie reprezentuje obiekt, który może lub nie mogą być niedostępne.|  
  
### <a name="structures"></a>Struktury  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[ChainInterfaces, struktura](../windows/chaininterfaces-structure.md)|Określa weryfikacji i inicjowania funkcje, które można zastosować do zestawu interfejsu identyfikatorów.|  
|[CloakedIid, struktura](../windows/cloakediid-structure.md)|Wskazuje, aby `RuntimeClass`, `Implements` i `ChainInterfaces` określonego interfejsu nie jest dostępny na liście IID szablonów.|  
|[Implements, struktura](../windows/implements-structure.md)|Implementuje `QueryInterface` i `GetIid` dla określonych interfejsów.|  
|[MixIn, struktura](../windows/mixin-structure.md)|Zapewnia, że klasa środowiska uruchomieniowego pochodzi z interfejsów środowiska wykonawczego systemu Windows, jeśli istnieje, a następnie klasycznego interfejsy modelu COM.|  
  
### <a name="functions"></a>Funkcje  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[ActivateInstance, funkcja](../windows/activateinstance-function.md)|Rejestruje i pobiera wystąpienia określonego typu zdefiniowane w identyfikatora dla określonej klasy.|  
|[AsWeak, funkcja](../windows/asweak-function.md)|Pobiera słabe odwołanie do określonego wystąpienia.|  
|[Funkcja wywołania zwrotnego](../windows/callback-function-windows-runtime-cpp-template-library.md)|Tworzy obiekt, którego funkcja członkowska jest metoda wywołania zwrotnego.|  
|[CreateActivationFactory, funkcja](../windows/createactivationfactory-function.md)|Tworzy fabrykę tworzy wystąpienia określonej klasy, które można aktywować przez środowisko wykonawcze systemu Windows.|  
|[CreateClassFactory, funkcja](../windows/createclassfactory-function.md)|Tworzy fabrykę tworzy wystąpienia określonej klasy.|  
|[GetActivationFactory, funkcja](../windows/getactivationfactory-function.md)|Pobiera fabryki aktywacji dla typu określonego przez parametr szablonu.|  
|[Make, funkcja](../windows/make-function.md)|Inicjuje określonej klasy środowiska wykonawczego systemu Windows.|  
  
### <a name="macros"></a>Makra  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Makra ActivatableClass](../windows/activatableclass-macros.md)|Wypełnia wewnętrznej pamięci podręcznej zawiera fabryka, która może utworzyć wystąpienie określonej klasy.|  
|[InspectableClass, makro](../windows/inspectableclass-macro.md)|Ustawia poziom nazwy i zaufania klasy środowiska wykonawczego.|  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteka szablonów języka C++ środowiska uruchomieniowego systemu Windows (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)