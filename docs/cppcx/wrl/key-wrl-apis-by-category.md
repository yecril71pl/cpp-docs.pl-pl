---
title: Kluczowe interfejsy API biblioteki WRL według kategorii
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 7367bacf-6b7c-4ecd-a0ce-a662db46fc66
ms.openlocfilehash: 8ac89f3286866ac61bac5ae256bdb448fe88f07d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213827"
---
# <a name="key-wrl-apis-by-category"></a>Kluczowe interfejsy API biblioteki WRL według kategorii

W poniższej tabeli wymieniono podstawowe C++ klasy środowisko wykonawcze systemu Windows biblioteki szablonów, struktury, funkcje i makra. Konstrukcje w przestrzeniach nazw pomocnika i klasach zostały pominięte. Te listy rozszerzają dokumentację interfejsu API, która jest uporządkowana według przestrzeni nazw.

## <a name="classes"></a>Klasy

|Tytuł|Opis|
|-----------|-----------------|
|[ActivationFactory, klasa](activationfactory-class.md)|Umożliwia aktywowanie co najmniej jednej klasy przez środowisko wykonawcze systemu Windows.|
|[AsyncBase, klasa](asyncbase-class.md)|Implementuje asynchroniczną maszynę stanu środowisko wykonawcze systemu Windows.|
|[ClassFactory, klasa](classfactory-class.md)|Implementuje podstawowe funkcje interfejsu `IClassFactory`.|
|[ComPtr, klasa](comptr-class.md)|Tworzy *inteligentny wskaźnik* typu, który reprezentuje interfejs określony przez parametr szablonu. ComPtr automatycznie utrzymuje liczbę odwołań dla podstawowego wskaźnika interfejsu i zwalnia interfejs, gdy liczba odwołań spadnie do zera.|
|[Event, klasa (Biblioteka szablonów języka C++ środowiska uruchomieniowego systemu Windows)](event-class-wrl.md)|Reprezentuje zdarzenie.|
|[EventSource, klasa](eventsource-class.md)|Reprezentuje zdarzenie. `EventSource` funkcje elementów członkowskich Dodaj, Usuń i Wywołaj procedury obsługi zdarzeń.|
|[FtmBase, klasa](ftmbase-class.md)|Reprezentuje obiekt organizatora wolnego wątku.|
|[HandleT, klasa](handlet-class.md)|Reprezentuje dojście do obiektu.|
|[HString, klasa](hstring-class.md)|Zapewnia obsługę manipulowania dojściami HSTRING.|
|[HStringReference, klasa](hstringreference-class.md)|Reprezentuje element HSTRING, który jest tworzony na podstawie istniejącego ciągu.|
|[Klasa modułu](module-class.md)|Reprezentuje kolekcję obiektów pokrewnych.|
|[Module::GenericReleaseNotifier, klasa](module-genericreleasenotifier-class.md)|Wywołuje program obsługi zdarzeń po wydaniu ostatniego obiektu w bieżącym module. Procedura obsługi zdarzeń jest określana na podstawie wyrażenia lambda, Funktor lub wskaźnika do funkcji.|
|[Module::MethodReleaseNotifier, klasa](module-methodreleasenotifier-class.md)|Wywołuje program obsługi zdarzeń po wydaniu ostatniego obiektu w bieżącym module. Program obsługi zdarzeń jest określany przez obiekt i jego element członkowski typu wskaźnik-a-metoda.|
|[Module::ReleaseNotifier, klasa](module-releasenotifier-class.md)|Wywołuje program obsługi zdarzeń po wydaniu ostatniego obiektu w module.|
|[RoInitializeWrapper, klasa](roinitializewrapper-class.md)|Inicjuje środowisko wykonawcze systemu Windows.|
|[RuntimeClass, klasa](runtimeclass-class.md)|Reprezentuje klasę wystąpienia, która dziedziczy określoną liczbę interfejsów i udostępnia określony środowisko wykonawcze systemu Windows, klasyczny COM i słabe wsparcie referencyjne.|
|[SimpleActivationFactory, klasa](simpleactivationfactory-class.md)|Zapewnia podstawowy mechanizm tworzenia środowisko wykonawcze systemu Windows lub klasycznej klasy bazowej modelu COM.|
|[SimpleClassFactory, klasa](simpleclassfactory-class.md)|Zapewnia podstawowy mechanizm tworzenia klasy bazowej.|
|[WeakRef, klasa](weakref-class.md)|Reprezentuje *słabe odwołanie* , które może być używane tylko przez środowisko wykonawcze systemu Windows, a nie klasyczny com. Słabe odwołanie reprezentuje obiekt, który może lub nie jest dostępny.|

## <a name="structures"></a>Struktury

|Tytuł|Opis|
|-----------|-----------------|
|[ChainInterfaces, struktura](chaininterfaces-structure.md)|Określa funkcje weryfikacji i inicjowania, które mogą być stosowane do zestawu identyfikatorów interfejsów.|
|[CloakedIid, struktura](cloakediid-structure.md)|Wskazuje `RuntimeClass`, `Implements` i `ChainInterfaces` szablonów, których określony interfejs nie jest dostępny na liście IID.|
|[Implements, struktura](implements-structure.md)|Implementuje `QueryInterface` i `GetIid` dla określonych interfejsów.|
|[MixIn, struktura](mixin-structure.md)|Zapewnia, że Klasa środowiska uruchomieniowego pochodzi z interfejsów środowisko wykonawcze systemu Windows, jeśli istnieje, a następnie do klasycznych interfejsów COM.|

## <a name="functions"></a>Funkcje

|Tytuł|Opis|
|-----------|-----------------|
|[ActivateInstance, funkcja](activateinstance-function.md)|Rejestruje i Pobiera wystąpienie określonego typu zdefiniowane w określonym IDENTYFIKATORze klasy.|
|[AsWeak, funkcja](asweak-function.md)|Pobiera słabe odwołanie do określonego wystąpienia.|
|[Funkcja wywołania zwrotnego](callback-function-wrl.md)|Tworzy obiekt, którego funkcja członkowska jest metodą wywołania zwrotnego.|
|[CreateActivationFactory, funkcja](createactivationfactory-function.md)|Tworzy fabrykę, która tworzy wystąpienia określonej klasy, które mogą być aktywowane przez środowisko wykonawcze systemu Windows.|
|[CreateClassFactory, funkcja](createclassfactory-function.md)|Tworzy fabrykę, która tworzy wystąpienia określonej klasy.|
|[GetActivationFactory, funkcja](getactivationfactory-function.md)|Pobiera fabrykę aktywacji dla typu określonego przez parametr szablonu.|
|[Make, funkcja](make-function.md)|Inicjuje określoną klasę środowisko wykonawcze systemu Windows.|

## <a name="macros"></a>Makra

|Tytuł|Opis|
|-----------|-----------------|
|[Makra ActivatableClass](activatableclass-macros.md)|Wypełnia wewnętrzną pamięć podręczną, która zawiera fabrykę, która może utworzyć wystąpienie określonej klasy.|
|[InspectableClass, makro](inspectableclass-macro.md)|Ustawia nazwę klasy środowiska uruchomieniowego i poziom zaufania.|

## <a name="see-also"></a>Zobacz też

[Biblioteka szablonów języka C++ środowiska uruchomieniowego systemu Windows (WRL)](windows-runtime-cpp-template-library-wrl.md)
