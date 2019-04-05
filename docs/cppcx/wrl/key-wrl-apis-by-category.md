---
title: Kluczowe interfejsy API biblioteki WRL według kategorii
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 7367bacf-6b7c-4ecd-a0ce-a662db46fc66
ms.openlocfilehash: f3065323c567c944dab12fc1ebbcbd6bb57127e9
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59039060"
---
# <a name="key-wrl-apis-by-category"></a>Kluczowe interfejsy API biblioteki WRL według kategorii

W poniższej tabeli wymieniono podstawowe klasy, struktury, funkcjami i makrami Biblioteka szablonów C++ środowiska wykonawczego Windows. Konstrukcje w pomocnika przestrzeni nazw i klas są pomijane. Te listy rozszerzyć dokumentacji interfejsu API, które są uporządkowane według przestrzeni nazw.

## <a name="classes"></a>Klasy

|Tytuł|Opis|
|-----------|-----------------|
|[ActivationFactory — Klasa](activationfactory-class.md)|Umożliwia co najmniej jedną klasę na uaktywnianie przez środowisko wykonawcze Windows.|
|[AsyncBase — Klasa](asyncbase-class.md)|Implementuje automatu stanów asynchronicznych środowiska wykonawczego Windows.|
|[ClassFactory — Klasa](classfactory-class.md)|Implementuje podstawowe funkcje `IClassFactory` interfejsu.|
|[ComPtr — Klasa](comptr-class.md)|Tworzy *inteligentny wskaźnik* typ, który reprezentuje interfejs określony przez parametr szablonu. ComPtr automatycznie przechowuje licznik odwołań dla podstawowego wskaźnika interfejsu i zwalnia interfejs gdy liczba odwołań osiąga zero.|
|[Event — Klasa (Biblioteka szablonów języka C++ środowiska wykonawczego systemu Windows)](event-class-wrl.md)|Przedstawia zdarzenie.|
|[EventSource — Klasa](eventsource-class.md)|Przedstawia zdarzenie. `EventSource` Funkcje Członkowskie dodawania, usuwania i wywoływanie programów obsługi zdarzeń.|
|[FtmBase — Klasa](ftmbase-class.md)|Reprezentuje obiekt bezwątkowego.|
|[HandleT — Klasa](handlet-class.md)|Reprezentuje uchwyt do obiektu.|
|[HString — Klasa](hstring-class.md)|Zapewnia obsługę manipulowania uchwytami HSTRING.|
|[HStringReference — Klasa](hstringreference-class.md)|Reprezentuje HSTRING, utworzony na podstawie istniejącego ciągu.|
|[Module — Klasa](module-class.md)|Reprezentuje kolekcję obiektów pokrewnych.|
|[Module::GenericReleaseNotifier — Klasa](module-genericreleasenotifier-class.md)|Wywołuje program obsługi zdarzeń po udostępnieniu ostatni obiekt w bieżącego modułu. Program obsługi zdarzeń jest określone w lambda, funktor lub wskaźnik do funkcji.|
|[Module::MethodReleaseNotifier — Klasa](module-methodreleasenotifier-class.md)|Wywołuje program obsługi zdarzeń po udostępnieniu ostatni obiekt w bieżącego modułu. Program obsługi zdarzeń jest określona przez obiekt i jego elementów członkowskich wskaźnika do metody.|
|[Module::ReleaseNotifier — Klasa](module-releasenotifier-class.md)|Wywołuje program obsługi zdarzeń po udostępnieniu ostatni obiekt w module.|
|[RoInitializeWrapper — Klasa](roinitializewrapper-class.md)|Inicjuje środowisko wykonawcze Windows.|
|[RuntimeClass — Klasa](runtimeclass-class.md)|Reprezentuje skonkretyzowaną klasę, która dziedziczy określoną liczbę interfejsów, a także określonego środowiska wykonawczego Windows, Klasyczny model COM i odwołanie tymczasowe wsparcia.|
|[SimpleActivationFactory — Klasa](simpleactivationfactory-class.md)|Udostępnia mechanizm podstawowych do utworzenia środowiska uruchomieniowego Windows lub klasycznego modelu COM klasy bazowej.|
|[SimpleClassFactory — Klasa](simpleclassfactory-class.md)|Zapewnia mechanizm podstawowych, aby utworzyć klasę bazową.|
|[WeakRef — Klasa](weakref-class.md)|Reprezentuje *słabe odwołanie* mogą służyć tylko Windows środowisko wykonawcze, nie Klasyczny model COM. Słabe odwołanie reprezentuje obiekt, który może być lub może być niedostępny.|

## <a name="structures"></a>Struktury

|Tytuł|Opis|
|-----------|-----------------|
|[ChainInterfaces — Struktura](chaininterfaces-structure.md)|Określa funkcje weryfikacji i inicjowania, które może odnosić się do zestawu interfejsu identyfikatorów.|
|[CloakedIid — Struktura](cloakediid-structure.md)|Wskazuje, aby `RuntimeClass`, `Implements` i `ChainInterfaces` określonego interfejsu nie jest dostępny na liście IID szablonów.|
|[Implements — Struktura](implements-structure.md)|Implementuje `QueryInterface` i `GetIid` dla określonych interfejsów.|
|[MixIn — Struktura](mixin-structure.md)|Zapewnia, że klasy środowiska uruchomieniowego pochodzi od klasy interfejsów Windows Runtime, jeśli istnieje, a następnie klasycznych interfejsów COM.|

## <a name="functions"></a>Funkcje

|Tytuł|Opis|
|-----------|-----------------|
|[ActivateInstance — Funkcja](activateinstance-function.md)|Rejestruje i pobiera wystąpienia danego typu zdefiniowane w identyfikatorze określonej klasy.|
|[AsWeak — Funkcja](asweak-function.md)|Pobiera słabe odwołanie do określonego wystąpienia.|
|[Callback — Funkcja](callback-function-wrl.md)|Tworzy obiekt, którego funkcja członkowska jest metodą wywołania zwrotnego.|
|[CreateActivationFactory — Funkcja](createactivationfactory-function.md)|Tworzy fabrykę, która tworzy wystąpienia określonej klasy, które można uaktywnić przez środowisko wykonawcze Windows.|
|[CreateClassFactory — Funkcja](createclassfactory-function.md)|Tworzy fabrykę, która tworzy wystąpienia określonej klasy.|
|[GetActivationFactory — Funkcja](getactivationfactory-function.md)|Pobiera fabrykę aktywacji dla typu określonego przez parametr szablonu.|
|[Make — Funkcja](make-function.md)|Inicjuje określonej klasy środowiska wykonawczego Windows.|

## <a name="macros"></a>Makra

|Tytuł|Opis|
|-----------|-----------------|
|[ActivatableClass Makra](activatableclass-macros.md)|Wypełnia wewnętrzną pamięć podręczną zawierającą fabryki, który można utworzyć wystąpienie określonej klasy.|
|[InspectableClass — Makro](inspectableclass-macro.md)|Ustawia poziom nazwy i zaufania klasy środowiska uruchomieniowego.|

## <a name="see-also"></a>Zobacz także

[Biblioteka szablonów języka C++ środowiska wykonawczego systemu Windows (WRL)](windows-runtime-cpp-template-library-wrl.md)