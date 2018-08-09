---
title: Microsoft::WRL Namespace | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
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
dev_langs:
- C++
helpviewer_keywords:
- WRL namespace
ms.assetid: 01118a8f-f564-4859-b87e-9444848585a1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b3b1f5d0472fbe9ceb997460b525153a9ad87a69
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40020255"
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
|`InhibitWeakReferencePolicy`|`RuntimeClassFlags<WinRt &#124; InhibitWeakReference>`|  
  
### <a name="classes"></a>Klasy  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[ActivationFactory, klasa](../windows/activationfactory-class.md)|Umożliwia co najmniej jedną klasę na uaktywnianie przez środowisko wykonawcze Windows.|  
|[AsyncBase, klasa](../windows/asyncbase-class.md)|Implementuje automatu stanów asynchronicznych środowiska wykonawczego Windows.|  
|[ClassFactory, klasa](../windows/classfactory-class.md)|Implementuje podstawowe funkcje `IClassFactory` interfejsu.|  
|[ComPtr, klasa](../windows/comptr-class.md)|Tworzy *inteligentny wskaźnik* typ, który reprezentuje interfejs określony przez parametr szablonu. ComPtr automatycznie przechowuje licznik odwołań dla podstawowego wskaźnika interfejsu i zwalnia interfejs gdy liczba odwołań osiąga zero.|  
|[DeferrableEventArgs, klasa](../windows/deferrableeventargs-class.md)|Klasa szablonu, używane dla typów argumentów zdarzenia dla odroczenia.|  
|[EventSource, klasa](../windows/eventsource-class.md)|Przedstawia zdarzenie. `EventSource` Funkcje Członkowskie dodawania, usuwania i wywoływanie programów obsługi zdarzeń.|  
|[FtmBase, klasa](../windows/ftmbase-class.md)|Reprezentuje obiekt bezwątkowego.|  
|[Klasa modułu](../windows/module-class.md)|Reprezentuje kolekcję obiektów pokrewnych.|  
|[RuntimeClass, klasa](../windows/runtimeclass-class.md)|Reprezentuje skonkretyzowaną klasę, która dziedziczy określoną liczbę interfejsów, a także określonego środowiska wykonawczego Windows, Klasyczny model COM i odwołanie tymczasowe wsparcia.|  
|[SimpleActivationFactory, klasa](../windows/simpleactivationfactory-class.md)|Udostępnia mechanizm podstawowych do utworzenia środowiska uruchomieniowego Windows lub klasycznego modelu COM klasy bazowej.|  
|[SimpleClassFactory, klasa](../windows/simpleclassfactory-class.md)|Zapewnia mechanizm podstawowych, aby utworzyć klasę bazową.|  
|[WeakRef, klasa](../windows/weakref-class.md)|Reprezentuje *słabe odwołanie* mogą służyć tylko Windows środowisko wykonawcze, nie Klasyczny model COM. Słabe odwołanie reprezentuje obiekt, który może być lub może być niedostępny.|  
  
### <a name="structures"></a>Struktury  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[ChainInterfaces, struktura](../windows/chaininterfaces-structure.md)|Określa funkcje weryfikacji i inicjowania, które może odnosić się do zestawu interfejsu identyfikatorów.|  
|[CloakedIid, struktura](../windows/cloakediid-structure.md)|Wskazuje, aby `RuntimeClass`, `Implements` i `ChainInterfaces` określonego interfejsu nie jest dostępny na liście IID szablonów.|  
|[Implements, struktura](../windows/implements-structure.md)|Implementuje `QueryInterface` i `GetIid` dla określonych interfejsów.|  
|[MixIn, struktura](../windows/mixin-structure.md)|Zapewnia, że klasy środowiska uruchomieniowego pochodzi od klasy interfejsów Windows Runtime, jeśli istnieje, a następnie klasycznych interfejsów COM.|  
|[RuntimeClassFlags, struktura](../windows/runtimeclassflags-structure.md)|Zawiera typ wystąpienia [RuntimeClass](../windows/runtimeclass-class.md).|  
  
### <a name="enumerations"></a>Wyliczenia  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[AsyncResultType, wyliczenie](../windows/asyncresulttype-enumeration.md)|Określa typ wyniku zwracanego przez `GetResults()` metody.|  
|[ModuleType, wyliczenie](../windows/moduletype-enumeration.md)|Określa, czy moduł powinien obsługiwać wewnątrz procesowego lub serwera spoza procesu.|  
|[RuntimeClassType, wyliczenie](../windows/runtimeclasstype-enumeration.md)|Określa typ [RuntimeClass](../windows/runtimeclass-class.md) wystąpienia, która jest obsługiwana.|  
  
### <a name="functions"></a>Funkcje  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[AsWeak, funkcja](../windows/asweak-function.md)|Pobiera słabe odwołanie do określonego wystąpienia.|  
|[Funkcja wywołania zwrotnego](../windows/callback-function-windows-runtime-cpp-template-library.md)|Tworzy obiekt, którego funkcja członkowska jest metodą wywołania zwrotnego.|  
|[CreateActivationFactory, funkcja](../windows/createactivationfactory-function.md)|Tworzy fabrykę, która tworzy wystąpienia określonej klasy, które można uaktywnić przez środowisko wykonawcze Windows.|  
|[CreateClassFactory, funkcja](../windows/createclassfactory-function.md)|Tworzy fabrykę, która tworzy wystąpienia określonej klasy.|  
|[Make, funkcja](../windows/make-function.md)|Inicjuje określonej klasy środowiska wykonawczego Windows.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** async.h client.h, corewrappers.h, event.h, ftm.h, implements.h, internal.h, module.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL::Wrappers, przestrzeń nazw](../windows/microsoft-wrl-wrappers-namespace.md)