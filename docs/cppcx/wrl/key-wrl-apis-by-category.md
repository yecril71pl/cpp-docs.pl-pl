---
title: Kluczowe interfejsy API biblioteki WRL według kategorii
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 7367bacf-6b7c-4ecd-a0ce-a662db46fc66
ms.openlocfilehash: f3065323c567c944dab12fc1ebbcbd6bb57127e9
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59039060"
---
# <a name="key-wrl-apis-by-category"></a>Kluczowe interfejsy API biblioteki WRL według kategorii

W poniższej tabeli wymieniono podstawowe klasy, struktury, funkcjami i makrami Biblioteka szablonów C++ środowiska wykonawczego Windows. Konstrukcje w pomocnika przestrzeni nazw i klas są pomijane. Te listy rozszerzyć dokumentacji interfejsu API, które są uporządkowane według przestrzeni nazw.

## <a name="classes"></a>Klasy

|Tytuł|Opis|
|-----------|-----------------|
|[ActivationFactory, klasa](activationfactory-class.md)|Umożliwia co najmniej jedną klasę na uaktywnianie przez środowisko wykonawcze Windows.|
|[AsyncBase, klasa](asyncbase-class.md)|Implementuje automatu stanów asynchronicznych środowiska wykonawczego Windows.|
|[ClassFactory, klasa](classfactory-class.md)|Implementuje podstawowe funkcje `IClassFactory` interfejsu.|
|[ComPtr, klasa](comptr-class.md)|Tworzy *inteligentny wskaźnik* typ, który reprezentuje interfejs określony przez parametr szablonu. ComPtr automatycznie przechowuje licznik odwołań dla podstawowego wskaźnika interfejsu i zwalnia interfejs gdy liczba odwołań osiąga zero.|
|[Event, klasa (Biblioteka szablonów języka C++ środowiska uruchomieniowego systemu Windows)](event-class-wrl.md)|Przedstawia zdarzenie.|
|[EventSource, klasa](eventsource-class.md)|Przedstawia zdarzenie. `EventSource` Funkcje Członkowskie dodawania, usuwania i wywoływanie programów obsługi zdarzeń.|
|[FtmBase, klasa](ftmbase-class.md)|Reprezentuje obiekt bezwątkowego.|
|[HandleT, klasa](handlet-class.md)|Reprezentuje uchwyt do obiektu.|
|[HString, klasa](hstring-class.md)|Zapewnia obsługę manipulowania uchwytami HSTRING.|
|[HStringReference, klasa](hstringreference-class.md)|Reprezentuje HSTRING, utworzony na podstawie istniejącego ciągu.|
|[Klasa modułu](module-class.md)|Reprezentuje kolekcję obiektów pokrewnych.|
|[Module::GenericReleaseNotifier, klasa](module-genericreleasenotifier-class.md)|Wywołuje program obsługi zdarzeń po udostępnieniu ostatni obiekt w bieżącego modułu. Program obsługi zdarzeń jest określone w lambda, funktor lub wskaźnik do funkcji.|
|[Module::MethodReleaseNotifier, klasa](module-methodreleasenotifier-class.md)|Wywołuje program obsługi zdarzeń po udostępnieniu ostatni obiekt w bieżącego modułu. Program obsługi zdarzeń jest określona przez obiekt i jego elementów członkowskich wskaźnika do metody.|
|[Module::ReleaseNotifier, klasa](module-releasenotifier-class.md)|Wywołuje program obsługi zdarzeń po udostępnieniu ostatni obiekt w module.|
|[RoInitializeWrapper, klasa](roinitializewrapper-class.md)|Inicjuje środowisko wykonawcze Windows.|
|[RuntimeClass, klasa](runtimeclass-class.md)|Reprezentuje skonkretyzowaną klasę, która dziedziczy określoną liczbę interfejsów, a także określonego środowiska wykonawczego Windows, Klasyczny model COM i odwołanie tymczasowe wsparcia.|
|[SimpleActivationFactory, klasa](simpleactivationfactory-class.md)|Udostępnia mechanizm podstawowych do utworzenia środowiska uruchomieniowego Windows lub klasycznego modelu COM klasy bazowej.|
|[SimpleClassFactory, klasa](simpleclassfactory-class.md)|Zapewnia mechanizm podstawowych, aby utworzyć klasę bazową.|
|[WeakRef, klasa](weakref-class.md)|Reprezentuje *słabe odwołanie* mogą służyć tylko Windows środowisko wykonawcze, nie Klasyczny model COM. Słabe odwołanie reprezentuje obiekt, który może być lub może być niedostępny.|

## <a name="structures"></a>Struktury

|Tytuł|Opis|
|-----------|-----------------|
|[ChainInterfaces, struktura](chaininterfaces-structure.md)|Określa funkcje weryfikacji i inicjowania, które może odnosić się do zestawu interfejsu identyfikatorów.|
|[CloakedIid, struktura](cloakediid-structure.md)|Wskazuje, aby `RuntimeClass`, `Implements` i `ChainInterfaces` określonego interfejsu nie jest dostępny na liście IID szablonów.|
|[Implements, struktura](implements-structure.md)|Implementuje `QueryInterface` i `GetIid` dla określonych interfejsów.|
|[MixIn, struktura](mixin-structure.md)|Zapewnia, że klasy środowiska uruchomieniowego pochodzi od klasy interfejsów Windows Runtime, jeśli istnieje, a następnie klasycznych interfejsów COM.|

## <a name="functions"></a>Funkcje

|Tytuł|Opis|
|-----------|-----------------|
|[ActivateInstance, funkcja](activateinstance-function.md)|Rejestruje i pobiera wystąpienia danego typu zdefiniowane w identyfikatorze określonej klasy.|
|[AsWeak, funkcja](asweak-function.md)|Pobiera słabe odwołanie do określonego wystąpienia.|
|[Funkcja wywołania zwrotnego](callback-function-wrl.md)|Tworzy obiekt, którego funkcja członkowska jest metodą wywołania zwrotnego.|
|[CreateActivationFactory, funkcja](createactivationfactory-function.md)|Tworzy fabrykę, która tworzy wystąpienia określonej klasy, które można uaktywnić przez środowisko wykonawcze Windows.|
|[CreateClassFactory, funkcja](createclassfactory-function.md)|Tworzy fabrykę, która tworzy wystąpienia określonej klasy.|
|[GetActivationFactory, funkcja](getactivationfactory-function.md)|Pobiera fabrykę aktywacji dla typu określonego przez parametr szablonu.|
|[Make, funkcja](make-function.md)|Inicjuje określonej klasy środowiska wykonawczego Windows.|

## <a name="macros"></a>Makra

|Tytuł|Opis|
|-----------|-----------------|
|[Makra ActivatableClass](activatableclass-macros.md)|Wypełnia wewnętrzną pamięć podręczną zawierającą fabryki, który można utworzyć wystąpienie określonej klasy.|
|[InspectableClass, makro](inspectableclass-macro.md)|Ustawia poziom nazwy i zaufania klasy środowiska uruchomieniowego.|

## <a name="see-also"></a>Zobacz także

[Biblioteka szablonów języka C++ środowiska uruchomieniowego systemu Windows (WRL)](windows-runtime-cpp-template-library-wrl.md)