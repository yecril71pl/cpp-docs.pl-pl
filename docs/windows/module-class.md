---
title: "Klasa modułu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::Module
dev_langs: C++
helpviewer_keywords: Module class
ms.assetid: dd67e3b8-c2e1-4f53-8c0f-565a140ba649
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d17e0dc79241fbd84e282b9cd8403259e34def0e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="module-class"></a>Module — Klasa
Reprezentuje kolekcję obiektów pokrewnych.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
template<  
   ModuleType moduleType  
>  
class Module;  
  
template<>  
class Module<InProc> : public Details::ModuleBase;  
  
template<>  
class Module<OutOfProc> : public Module<InProc>;  
```  
  
#### <a name="parameters"></a>Parametry  
 `moduleType`  
 Kombinacja jednego lub więcej [ModuleType](../windows/moduletype-enumeration.md) wartości wyliczenia.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="protected-classes"></a>Klasy chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Module::GenericReleaseNotifier, klasa](../windows/module-genericreleasenotifier-class.md)|Wywołuje program obsługi zdarzeń po zwolnieniu ostatni obiekt w bieżącego modułu. Program obsługi zdarzeń jest określona przez na lambda, obiekt lub wskaźnik do funkcji.|  
|[Module::MethodReleaseNotifier, klasa](../windows/module-methodreleasenotifier-class.md)|Wywołuje program obsługi zdarzeń po zwolnieniu ostatni obiekt w bieżącego modułu. Program obsługi zdarzeń jest określona przez obiekt i jego elementów członkowskich wskaźnika do metody.|  
|[Module::ReleaseNotifier, klasa](../windows/module-releasenotifier-class.md)|Wywołuje program obsługi zdarzeń po zwolnieniu ostatni obiekt w module.|  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Module::~Module, destruktor](../windows/module-tilde-module-destructor.md)|Deinitializes bieżącego wystąpienia klasy modułu.|  
  
### <a name="protected-constructors"></a>Konstruktory chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Module::Module, konstruktor](../windows/module-module-constructor.md)|Inicjuje nowe wystąpienie klasy modułu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Module::Create, metoda](../windows/module-create-method.md)|Tworzy wystąpienie modułu.|  
|[Module::DecrementObjectCount, metoda](../windows/module-decrementobjectcount-method.md)|Zmniejsza liczbę obiektów śledzone przez moduł.|  
|[Module::GetActivationFactory, metoda](../windows/module-getactivationfactory-method.md)|Pobiera fabryki aktywacji dla modułu.|  
|[Module::GetClassObject, metoda](../windows/module-getclassobject-method.md)|Pobiera fabryki klas pamięci podręcznej.|  
|[Module::GetModule, metoda](../windows/module-getmodule-method.md)|Tworzy wystąpienie modułu.|  
|[Module::GetObjectCount, metoda](../windows/module-getobjectcount-method.md)|Pobiera liczbę obiektów zarządzanych przez ten moduł.|  
|[Module::IncrementObjectCount, metoda](../windows/module-incrementobjectcount-method.md)|Zwiększa liczbę obiektów śledzone przez moduł.|  
|[Module::RegisterCOMObject, metoda](../windows/module-registercomobject-method.md)|Rejestruje jednego lub większej liczby obiektów COM, więc inne aplikacje mogą łączyć się z nimi.|  
|[Module::RegisterObjects, metoda](../windows/module-registerobjects-method.md)|Rejestruje obiektów COM lub środowiska wykonawczego systemu Windows, więc inne aplikacje mogą łączyć się z nimi.|  
|[Module::RegisterWinRTObject, metoda](../windows/module-registerwinrtobject-method.md)|Rejestruje co najmniej jeden obiekt środowiska wykonawczego systemu Windows, więc inne aplikacje mogą łączyć się z nimi.|  
|[Module::Terminate, metoda](../windows/module-terminate-method.md)|Powoduje, że fabryki wszystkie utworzone przez moduł zamknięcia.|  
|[Module::UnregisterCOMObject, metoda](../windows/module-unregistercomobject-method.md)|Wyrejestrowuje co najmniej jeden obiekt COM, co zapobiega inne aplikacje połączyć się z nimi.|  
|[Module::UnregisterObjects, metoda](../windows/module-unregisterobjects-method.md)|Wyrejestrowuje obiektów określony moduł, dzięki czemu inne aplikacje nie mogą łączyć się je.|  
|[Module::UnregisterWinRTObject, metoda](../windows/module-unregisterwinrtobject-method.md)|Wyrejestrowuje co najmniej jeden obiekt środowiska wykonawczego systemu Windows, dzięki czemu inne aplikacje nie mogą łączyć się je.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Module::Create, metoda](../windows/module-create-method.md)|Tworzy wystąpienie modułu.|  
  
### <a name="protected-data-members"></a>Dane chronione elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Module::objectCount_, składowa danych](../windows/module-objectcount-data-member.md)|Przechowuje informacje o ile klasy zostały utworzone z [upewnij](../windows/make-function.md) funkcji.|  
|[Module::releaseNotifier_, składowa danych](../windows/module-releasenotifier-data-member.md)|Zawiera wskaźnik do obiektu ReleaseNotifier.|  
  
### <a name="macros"></a>Makra  
  
|||  
|-|-|  
|[ActivatableClass](../windows/activatableclass-macros.md)|Wypełnia wewnętrznej pamięci podręcznej zawiera fabryka, która może utworzyć wystąpienie określonej klasy. To makro określa parametrów identyfikator domyślnych ustawień fabrycznych i grupy.|  
|[ActivatableClassWithFactory](../windows/activatableclass-macros.md)|Wypełnia wewnętrznej pamięci podręcznej zawiera fabryka, która może utworzyć wystąpienie określonej klasy. To makro można określić parametru określonego fabryki.|  
|[ActivatableClassWithFactoryEx](../windows/activatableclass-macros.md)|Wypełnia wewnętrznej pamięci podręcznej zawiera fabryka, która może utworzyć wystąpienie określonej klasy. To makro umożliwia określenie konkretnego fabryki i parametry Identyfikatora grupy.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `ModuleBase`  
  
 `Module`  
  
 `Module`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL, przestrzeń nazw](../windows/microsoft-wrl-namespace.md)