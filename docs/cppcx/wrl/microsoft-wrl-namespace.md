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
ms.openlocfilehash: 749469c7ae2acf3a0da92d24a51bbfca9b68971d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392027"
---
# <a name="microsoftwrl-namespace"></a>Microsoft::WRL — Przestrzeń nazw

Definiuje podstawowe typy, które tworzą Biblioteka szablonów C++ środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```cpp
namespace Microsoft::WRL;
```

## <a name="members"></a>Elementy członkowskie

### <a name="typedefs"></a>Typedefs

|Nazwa|Opis|
|----------|-----------------|
|`InhibitWeakReferencePolicy`|`RuntimeClassFlags<WinRt | InhibitWeakReference>`|

### <a name="classes"></a>Klasy

|Nazwa|Opis|
|----------|-----------------|
|[ActivationFactory, klasa](activationfactory-class.md)|Umożliwia co najmniej jedną klasę na uaktywnianie przez środowisko wykonawcze Windows.|
|[AsyncBase, klasa](asyncbase-class.md)|Implementuje automatu stanów asynchronicznych środowiska wykonawczego Windows.|
|[ClassFactory, klasa](classfactory-class.md)|Implementuje podstawowe funkcje `IClassFactory` interfejsu.|
|[ComPtr, klasa](comptr-class.md)|Tworzy *inteligentny wskaźnik* typ, który reprezentuje interfejs określony przez parametr szablonu. ComPtr automatycznie przechowuje licznik odwołań dla podstawowego wskaźnika interfejsu i zwalnia interfejs gdy liczba odwołań osiąga zero.|
|[DeferrableEventArgs, klasa](deferrableeventargs-class.md)|Klasa szablonu, używane dla typów argumentów zdarzenia dla odroczenia.|
|[EventSource, klasa](eventsource-class.md)|Przedstawia zdarzenie. `EventSource` Funkcje Członkowskie dodawania, usuwania i wywoływanie programów obsługi zdarzeń.|
|[FtmBase, klasa](ftmbase-class.md)|Reprezentuje obiekt bezwątkowego.|
|[Klasa modułu](module-class.md)|Reprezentuje kolekcję obiektów pokrewnych.|
|[RuntimeClass, klasa](runtimeclass-class.md)|Reprezentuje skonkretyzowaną klasę, która dziedziczy określoną liczbę interfejsów, a także określonego środowiska wykonawczego Windows, Klasyczny model COM i odwołanie tymczasowe wsparcia.|
|[SimpleActivationFactory, klasa](simpleactivationfactory-class.md)|Udostępnia mechanizm podstawowych do utworzenia środowiska uruchomieniowego Windows lub klasycznego modelu COM klasy bazowej.|
|[SimpleClassFactory, klasa](simpleclassfactory-class.md)|Zapewnia mechanizm podstawowych, aby utworzyć klasę bazową.|
|[WeakRef, klasa](weakref-class.md)|Reprezentuje *słabe odwołanie* mogą służyć tylko Windows środowisko wykonawcze, nie Klasyczny model COM. Słabe odwołanie reprezentuje obiekt, który może być lub może być niedostępny.|

### <a name="structures"></a>Struktury

|Nazwa|Opis|
|----------|-----------------|
|[ChainInterfaces, struktura](chaininterfaces-structure.md)|Określa funkcje weryfikacji i inicjowania, które może odnosić się do zestawu interfejsu identyfikatorów.|
|[CloakedIid, struktura](cloakediid-structure.md)|Wskazuje, aby `RuntimeClass`, `Implements` i `ChainInterfaces` określonego interfejsu nie jest dostępny na liście IID szablonów.|
|[Implements, struktura](implements-structure.md)|Implementuje `QueryInterface` i `GetIid` dla określonych interfejsów.|
|[MixIn, struktura](mixin-structure.md)|Zapewnia, że klasy środowiska uruchomieniowego pochodzi od klasy interfejsów Windows Runtime, jeśli istnieje, a następnie klasycznych interfejsów COM.|
|[RuntimeClassFlags, struktura](runtimeclassflags-structure.md)|Zawiera typ wystąpienia [RuntimeClass](runtimeclass-class.md).|

### <a name="enumerations"></a>Wyliczenia

|Nazwa|Opis|
|----------|-----------------|
|[AsyncResultType, wyliczenie](asyncresulttype-enumeration.md)|Określa typ wyniku zwracanego przez `GetResults()` metody.|
|[ModuleType, wyliczenie](moduletype-enumeration.md)|Określa, czy moduł powinien obsługiwać wewnątrz procesowego lub serwera spoza procesu.|
|[RuntimeClassType, wyliczenie](runtimeclasstype-enumeration.md)|Określa typ [RuntimeClass](runtimeclass-class.md) wystąpienia, która jest obsługiwana.|

### <a name="functions"></a>Funkcje

|Nazwa|Opis|
|----------|-----------------|
|[AsWeak, funkcja](asweak-function.md)|Pobiera słabe odwołanie do określonego wystąpienia.|
|[Callback — Funkcja (WRL)](callback-function-wrl.md)|Tworzy obiekt, którego funkcja członkowska jest metodą wywołania zwrotnego.|
|[CreateActivationFactory, funkcja](createactivationfactory-function.md)|Tworzy fabrykę, która tworzy wystąpienia określonej klasy, które można uaktywnić przez środowisko wykonawcze Windows.|
|[CreateClassFactory, funkcja](createclassfactory-function.md)|Tworzy fabrykę, która tworzy wystąpienia określonej klasy.|
|[Make, funkcja](make-function.md)|Inicjuje określonej klasy środowiska wykonawczego Windows.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** async.h client.h, corewrappers.h, event.h, ftm.h, implements.h, internal.h, module.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz także

[Microsoft::WRL::Wrappers, przestrzeń nazw](microsoft-wrl-wrappers-namespace.md)