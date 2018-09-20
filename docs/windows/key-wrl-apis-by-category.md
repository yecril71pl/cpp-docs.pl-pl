---
title: Kluczowe interfejsy API biblioteki WRL według kategorii | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: 7367bacf-6b7c-4ecd-a0ce-a662db46fc66
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d79888a58e5fc6d6911c4cc123877c1537f22cf1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46441931"
---
# <a name="key-wrl-apis-by-category"></a>Kluczowe interfejsy API biblioteki WRL według kategorii
W poniższej tabeli wymieniono podstawowe klasy, struktury, funkcjami i makrami Biblioteka szablonów C++ środowiska wykonawczego Windows. Konstrukcje w pomocnika przestrzeni nazw i klas są pomijane. Te listy rozszerzyć dokumentacji interfejsu API, które są uporządkowane według przestrzeni nazw.
  
### <a name="classes"></a>Klasy
  
|Tytuł|Opis|
|-----------|-----------------|
|[ActivationFactory, klasa](../windows/activationfactory-class.md)|Umożliwia co najmniej jedną klasę na uaktywnianie przez środowisko wykonawcze Windows.|
|[AsyncBase, klasa](../windows/asyncbase-class.md)|Implementuje automatu stanów asynchronicznych środowiska wykonawczego Windows.|
|[ClassFactory, klasa](../windows/classfactory-class.md)|Implementuje podstawowe funkcje `IClassFactory` interfejsu.|
|[ComPtr, klasa](../windows/comptr-class.md)|Tworzy *inteligentny wskaźnik* typ, który reprezentuje interfejs określony przez parametr szablonu. ComPtr automatycznie przechowuje licznik odwołań dla podstawowego wskaźnika interfejsu i zwalnia interfejs gdy liczba odwołań osiąga zero.|
|[Event, klasa (Biblioteka szablonów języka C++ środowiska uruchomieniowego systemu Windows)](../windows/event-class-windows-runtime-cpp-template-library.md)|Przedstawia zdarzenie.|
|[EventSource, klasa](../windows/eventsource-class.md)|Przedstawia zdarzenie. `EventSource` Funkcje Członkowskie dodawania, usuwania i wywoływanie programów obsługi zdarzeń.|
|[FtmBase, klasa](../windows/ftmbase-class.md)|Reprezentuje obiekt bezwątkowego.|
|[HandleT, klasa](../windows/handlet-class.md)|Reprezentuje uchwyt do obiektu.|
|[HString, klasa](../windows/hstring-class.md)|Zapewnia obsługę manipulowania uchwytami HSTRING.|
|[HStringReference, klasa](../windows/hstringreference-class.md)|Reprezentuje HSTRING, utworzony na podstawie istniejącego ciągu.|
|[Klasa modułu](../windows/module-class.md)|Reprezentuje kolekcję obiektów pokrewnych.|
|[Module::GenericReleaseNotifier, klasa](../windows/module-genericreleasenotifier-class.md)|Wywołuje program obsługi zdarzeń po udostępnieniu ostatni obiekt w bieżącego modułu. Program obsługi zdarzeń jest określone w lambda, funktor lub wskaźnik do funkcji.|
|[Module::MethodReleaseNotifier, klasa](../windows/module-methodreleasenotifier-class.md)|Wywołuje program obsługi zdarzeń po udostępnieniu ostatni obiekt w bieżącego modułu. Program obsługi zdarzeń jest określona przez obiekt i jego elementów członkowskich wskaźnika do metody.|
|[Module::ReleaseNotifier, klasa](../windows/module-releasenotifier-class.md)|Wywołuje program obsługi zdarzeń po udostępnieniu ostatni obiekt w module.|
|[RoInitializeWrapper, klasa](../windows/roinitializewrapper-class.md)|Inicjuje środowisko wykonawcze Windows.|
|[RuntimeClass, klasa](../windows/runtimeclass-class.md)|Reprezentuje skonkretyzowaną klasę, która dziedziczy określoną liczbę interfejsów, a także określonego środowiska wykonawczego Windows, Klasyczny model COM i odwołanie tymczasowe wsparcia.|
|[SimpleActivationFactory, klasa](../windows/simpleactivationfactory-class.md)|Udostępnia mechanizm podstawowych do utworzenia środowiska uruchomieniowego Windows lub klasycznego modelu COM klasy bazowej.|
|[SimpleClassFactory, klasa](../windows/simpleclassfactory-class.md)|Zapewnia mechanizm podstawowych, aby utworzyć klasę bazową.|
|[WeakRef, klasa](../windows/weakref-class.md)|Reprezentuje *słabe odwołanie* mogą służyć tylko Windows środowisko wykonawcze, nie Klasyczny model COM. Słabe odwołanie reprezentuje obiekt, który może być lub może być niedostępny.|
  
### <a name="structures"></a>Struktury
  
|Tytuł|Opis|
|-----------|-----------------|
|[ChainInterfaces, struktura](../windows/chaininterfaces-structure.md)|Określa funkcje weryfikacji i inicjowania, które może odnosić się do zestawu interfejsu identyfikatorów.|
|[CloakedIid, struktura](../windows/cloakediid-structure.md)|Wskazuje, aby `RuntimeClass`, `Implements` i `ChainInterfaces` określonego interfejsu nie jest dostępny na liście IID szablonów.|
|[Implements, struktura](../windows/implements-structure.md)|Implementuje `QueryInterface` i `GetIid` dla określonych interfejsów.|
|[MixIn, struktura](../windows/mixin-structure.md)|Zapewnia, że klasy środowiska uruchomieniowego pochodzi od klasy interfejsów Windows Runtime, jeśli istnieje, a następnie klasycznych interfejsów COM.|
  
### <a name="functions"></a>Funkcje
  
|Tytuł|Opis|
|-----------|-----------------|
|[ActivateInstance, funkcja](../windows/activateinstance-function.md)|Rejestruje i pobiera wystąpienia danego typu zdefiniowane w identyfikatorze określonej klasy.|
|[AsWeak, funkcja](../windows/asweak-function.md)|Pobiera słabe odwołanie do określonego wystąpienia.|
|[Funkcja wywołania zwrotnego](../windows/callback-function-windows-runtime-cpp-template-library.md)|Tworzy obiekt, którego funkcja członkowska jest metodą wywołania zwrotnego.|
|[CreateActivationFactory, funkcja](../windows/createactivationfactory-function.md)|Tworzy fabrykę, która tworzy wystąpienia określonej klasy, które można uaktywnić przez środowisko wykonawcze Windows.|
|[CreateClassFactory, funkcja](../windows/createclassfactory-function.md)|Tworzy fabrykę, która tworzy wystąpienia określonej klasy.|
|[GetActivationFactory, funkcja](../windows/getactivationfactory-function.md)|Pobiera fabrykę aktywacji dla typu określonego przez parametr szablonu.|
|[Make, funkcja](../windows/make-function.md)|Inicjuje określonej klasy środowiska wykonawczego Windows.|
  
### <a name="macros"></a>Makra
  
|Tytuł|Opis|
|-----------|-----------------|
|[Makra ActivatableClass](../windows/activatableclass-macros.md)|Wypełnia wewnętrzną pamięć podręczną zawierającą fabryki, który można utworzyć wystąpienie określonej klasy.|
|[InspectableClass, makro](../windows/inspectableclass-macro.md)|Ustawia poziom nazwy i zaufania klasy środowiska uruchomieniowego.|
  
## <a name="see-also"></a>Zobacz też

[Biblioteka szablonów języka C++ środowiska uruchomieniowego systemu Windows (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)