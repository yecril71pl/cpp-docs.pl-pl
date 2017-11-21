---
title: "Microsoft::wrl — Namespace | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
helpviewer_keywords: WRL namespace
ms.assetid: 01118a8f-f564-4859-b87e-9444848585a1
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7b3c3bef713bd63b7b82761ce36ab039556e63c0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="microsoftwrl-namespace"></a>Microsoft::WRL — Przestrzeń nazw
Definiuje podstawowe typy, które tworzą Biblioteka szablonów C++ środowiska wykonawczego systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
|[Activationfactory — klasa](../windows/activationfactory-class.md)|Umożliwia co najmniej jedną klasę do aktywacji przez środowisko wykonawcze systemu Windows.|  
|[Asyncbase — klasa](../windows/asyncbase-class.md)|Implementuje automatu stanów asynchroniczne środowiska wykonawczego systemu Windows.|  
|[ClassFactory — klasa](../windows/classfactory-class.md)|Implementuje podstawowych funkcji `IClassFactory` interfejsu.|  
|[Comptr — klasa](../windows/comptr-class.md)|Tworzy *wskaźnika inteligentnego* typu, który reprezentuje interfejs określonej przez parametr szablonu. Comptr — automatycznie przechowuje licznika odwołań do podstawowej wskaźnika interfejsu i zwalnia interfejsu, gdy liczba odwołań do zera.|  
|[Deferrableeventargs — klasa](../windows/deferrableeventargs-class.md)|Klasy szablonów używane dla typów argumentów zdarzenia dla odroczenia.|  
|[EventSource — klasa](../windows/eventsource-class.md)|Reprezentuje zdarzenie. `EventSource`Funkcje Członkowskie dodawania, usuwania i wywołanie procedury obsługi zdarzeń.|  
|[Ftmbase — klasa](../windows/ftmbase-class.md)|Reprezentuje obiekt opcja.|  
|[Klasa modułu](../windows/module-class.md)|Reprezentuje kolekcję obiektów pokrewnych.|  
|[Runtimeclass — klasa](../windows/runtimeclass-class.md)|Reprezentuje wystąpień klasy, która dziedziczy określona liczba interfejsów i zapewnia określonego środowiska wykonawczego systemu Windows, klasycznego modelu COM i obsługa słabe odwołanie.|  
|[Simpleactivationfactory — klasa](../windows/simpleactivationfactory-class.md)|Udostępnia mechanizm podstawowych do utworzenia środowiska wykonawczego systemu Windows lub klasycznego modelu COM klasy podstawowej.|  
|[Simpleclassfactory — klasa](../windows/simpleclassfactory-class.md)|Udostępnia mechanizm podstawowych, aby utworzyć klasę podstawową.|  
|[Weakref — klasa](../windows/weakref-class.md)|Reprezentuje *słabe odwołanie* które mogą być używane przez tylko środowiska uruchomieniowego systemu Windows, nie klasycznego modelu COM. Słabe odwołanie reprezentuje obiekt, który może lub nie mogą być niedostępne.|  
  
### <a name="structures"></a>Struktury  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Chaininterfaces — struktura](../windows/chaininterfaces-structure.md)|Określa weryfikacji i inicjowania funkcje, które można zastosować do zestawu interfejsu identyfikatorów.|  
|[Cloakediid — struktura](../windows/cloakediid-structure.md)|Wskazuje szablonów runtimeclass — i implementuje chaininterfaces — określonego interfejsu nie jest dostępny na liście IID.|  
|[Implements — struktura](../windows/implements-structure.md)|Implementuje metody QueryInterface i GetIid dla określonych interfejsów.|  
|[Mixin — struktura](../windows/mixin-structure.md)|Zapewnia, że klasa środowiska uruchomieniowego pochodzi z interfejsów środowiska wykonawczego systemu Windows, jeśli istnieje, a następnie klasycznego interfejsy modelu COM.|  
|[Runtimeclassflags — struktura](../windows/runtimeclassflags-structure.md)|Zawiera typ wystąpienia [runtimeclass —](../windows/runtimeclass-class.md).|  
  
### <a name="enumerations"></a>Wyliczenia  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Asyncresulttype — wyliczenie](../windows/asyncresulttype-enumeration.md)|Określa typ wyniku zwracany przez metodę GetResults().|  
|[ModuleType — wyliczenie](../windows/moduletype-enumeration.md)|Określa, czy moduł powinien obsługiwać server wewnątrzprocesowe lub serwer poza procesem.|  
|[Runtimeclasstype — wyliczenie](../windows/runtimeclasstype-enumeration.md)|Określa typ [runtimeclass —](../windows/runtimeclass-class.md) wystąpienia, która jest obsługiwana.|  
  
### <a name="functions"></a>Funkcje  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Asweak — funkcja](../windows/asweak-function.md)|Pobiera słabe odwołanie do określonego wystąpienia.|  
|[Funkcja wywołania zwrotnego](../windows/callback-function-windows-runtime-cpp-template-library.md)|Tworzy obiekt, którego funkcja członkowska jest metoda wywołania zwrotnego.|  
|[Createactivationfactory — funkcja](../windows/createactivationfactory-function.md)|Tworzy fabrykę tworzy wystąpienia określonej klasy, które można aktywować przez środowisko wykonawcze systemu Windows.|  
|[Createclassfactory — funkcja](../windows/createclassfactory-function.md)|Tworzy fabrykę tworzy wystąpienia określonej klasy.|  
|[Make — funkcja](../windows/make-function.md)|Inicjuje określonej klasy środowiska wykonawczego systemu Windows.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** async.h, client.h, corewrappers.h, event.h, ftm.h, implements.h, internal.h, module.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::wrl:: wrappers — Namespace](../windows/microsoft-wrl-wrappers-namespace.md)