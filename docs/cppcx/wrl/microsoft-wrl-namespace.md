---
title: Microsoft::WRL — Przestrzeń nazw
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL
- module/Microsoft::WRL
- async/Microsoft::WRL
- internal/Microsoft::WRL
- event/Microsoft::WRL
- ftm/Microsoft::WRL
- client/Microsoft::WRL
- corewrappers/Microsoft::WRL
helpviewer_keywords:
- WRL namespace
ms.assetid: 01118a8f-f564-4859-b87e-9444848585a1
ms.openlocfilehash: c92251dacbfa17e8f1ac0cbdc41aa9b06118ac91
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213775"
---
# <a name="microsoftwrl-namespace"></a>Microsoft::WRL — Przestrzeń nazw

Definiuje podstawowe typy, które tworzą środowisko wykonawcze systemu Windows C++ biblioteki szablonów.

## <a name="syntax"></a>Składnia

```cpp
namespace Microsoft::WRL;
```

## <a name="members"></a>Members

### <a name="typedefs"></a>Typedefs

|Name (Nazwa)|Opis|
|----------|-----------------|
|`InhibitWeakReferencePolicy`|`RuntimeClassFlags<WinRt | InhibitWeakReference>`|

### <a name="classes"></a>Klasy

|Name (Nazwa)|Opis|
|----------|-----------------|
|[ActivationFactory, klasa](activationfactory-class.md)|Umożliwia aktywowanie co najmniej jednej klasy przez środowisko wykonawcze systemu Windows.|
|[AsyncBase, klasa](asyncbase-class.md)|Implementuje asynchroniczną maszynę stanu środowisko wykonawcze systemu Windows.|
|[ClassFactory, klasa](classfactory-class.md)|Implementuje podstawowe funkcje interfejsu `IClassFactory`.|
|[ComPtr, klasa](comptr-class.md)|Tworzy *inteligentny wskaźnik* typu, który reprezentuje interfejs określony przez parametr szablonu. ComPtr automatycznie utrzymuje liczbę odwołań dla podstawowego wskaźnika interfejsu i zwalnia interfejs, gdy liczba odwołań spadnie do zera.|
|[DeferrableEventArgs, klasa](deferrableeventargs-class.md)|Klasa szablonu używana dla typów argumentów zdarzeń dla odroczeń.|
|[EventSource, klasa](eventsource-class.md)|Reprezentuje zdarzenie. `EventSource` funkcje elementów członkowskich Dodaj, Usuń i Wywołaj procedury obsługi zdarzeń.|
|[FtmBase, klasa](ftmbase-class.md)|Reprezentuje obiekt organizatora wolnego wątku.|
|[Klasa modułu](module-class.md)|Reprezentuje kolekcję obiektów pokrewnych.|
|[RuntimeClass, klasa](runtimeclass-class.md)|Reprezentuje klasę wystąpienia, która dziedziczy określoną liczbę interfejsów i udostępnia określony środowisko wykonawcze systemu Windows, klasyczny COM i słabe wsparcie referencyjne.|
|[SimpleActivationFactory, klasa](simpleactivationfactory-class.md)|Zapewnia podstawowy mechanizm tworzenia środowisko wykonawcze systemu Windows lub klasycznej klasy bazowej modelu COM.|
|[SimpleClassFactory, klasa](simpleclassfactory-class.md)|Zapewnia podstawowy mechanizm tworzenia klasy bazowej.|
|[WeakRef, klasa](weakref-class.md)|Reprezentuje *słabe odwołanie* , które może być używane tylko przez środowisko wykonawcze systemu Windows, a nie klasyczny com. Słabe odwołanie reprezentuje obiekt, który może lub nie jest dostępny.|

### <a name="structures"></a>Struktury

|Name (Nazwa)|Opis|
|----------|-----------------|
|[ChainInterfaces, struktura](chaininterfaces-structure.md)|Określa funkcje weryfikacji i inicjowania, które mogą być stosowane do zestawu identyfikatorów interfejsów.|
|[CloakedIid, struktura](cloakediid-structure.md)|Wskazuje `RuntimeClass`, `Implements` i `ChainInterfaces` szablonów, których określony interfejs nie jest dostępny na liście IID.|
|[Implements, struktura](implements-structure.md)|Implementuje `QueryInterface` i `GetIid` dla określonych interfejsów.|
|[MixIn, struktura](mixin-structure.md)|Zapewnia, że Klasa środowiska uruchomieniowego pochodzi z interfejsów środowisko wykonawcze systemu Windows, jeśli istnieje, a następnie do klasycznych interfejsów COM.|
|[RuntimeClassFlags, struktura](runtimeclassflags-structure.md)|Zawiera typ wystąpienia elementu [RuntimeClass](runtimeclass-class.md).|

### <a name="enumerations"></a>Wyliczenia

|Name (Nazwa)|Opis|
|----------|-----------------|
|[AsyncResultType, wyliczenie](asyncresulttype-enumeration.md)|Określa typ wyniku zwróconego przez metodę `GetResults()`.|
|[ModuleType, wyliczenie](moduletype-enumeration.md)|Określa, czy moduł powinien obsługiwać serwer w toku, czy też poza procesem.|
|[RuntimeClassType, wyliczenie](runtimeclasstype-enumeration.md)|Określa typ wystąpienia [RuntimeClass](runtimeclass-class.md) , które jest obsługiwane.|

### <a name="functions"></a>Funkcje

|Name (Nazwa)|Opis|
|----------|-----------------|
|[AsWeak, funkcja](asweak-function.md)|Pobiera słabe odwołanie do określonego wystąpienia.|
|[Callback — Funkcja (WRL)](callback-function-wrl.md)|Tworzy obiekt, którego funkcja członkowska jest metodą wywołania zwrotnego.|
|[CreateActivationFactory, funkcja](createactivationfactory-function.md)|Tworzy fabrykę, która tworzy wystąpienia określonej klasy, które mogą być aktywowane przez środowisko wykonawcze systemu Windows.|
|[CreateClassFactory, funkcja](createclassfactory-function.md)|Tworzy fabrykę, która tworzy wystąpienia określonej klasy.|
|[Make, funkcja](make-function.md)|Inicjuje określoną klasę środowisko wykonawcze systemu Windows.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** Async. h, Client. h, corewrappers. h, Event. h, FTM. h, implementuje. h, Internal. h, module. h

**Przestrzeń nazw:** Microsoft:: WRL

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL::Wrappers, przestrzeń nazw](microsoft-wrl-wrappers-namespace.md)
