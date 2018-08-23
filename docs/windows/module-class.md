---
title: Klasa modułu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module
dev_langs:
- C++
helpviewer_keywords:
- Module class
ms.assetid: dd67e3b8-c2e1-4f53-8c0f-565a140ba649
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2ae36838a1375b541951122bb00b522cf320650d
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42599758"
---
# <a name="module-class"></a>Module — Klasa

Reprezentuje kolekcję obiektów pokrewnych.

## <a name="syntax"></a>Składnia

```cpp
template<ModuleType moduleType>
class Module;

template<>
class Module<InProc> : public Details::ModuleBase;

template<>
class Module<OutOfProc> : public Module<InProc>;
```

### <a name="parameters"></a>Parametry

*Typ modułu*  
Kombinacji jednego lub więcej [ModuleType](../windows/moduletype-enumeration.md) wartości wyliczenia.

## <a name="members"></a>Elementy członkowskie

### <a name="protected-classes"></a>Klasy chronionych

|Nazwa|Opis|
|----------|-----------------|
|[Module::GenericReleaseNotifier, klasa](../windows/module-genericreleasenotifier-class.md)|Wywołuje program obsługi zdarzeń po udostępnieniu ostatni obiekt w bieżącego modułu. Program obsługi zdarzeń jest określone w lambda, funktor lub wskaźnik do funkcji.|
|[Module::MethodReleaseNotifier, klasa](../windows/module-methodreleasenotifier-class.md)|Wywołuje program obsługi zdarzeń po udostępnieniu ostatni obiekt w bieżącego modułu. Program obsługi zdarzeń jest określona przez obiekt i jego elementów członkowskich wskaźnika do metody.|
|[Module::ReleaseNotifier, klasa](../windows/module-releasenotifier-class.md)|Wywołuje program obsługi zdarzeń po udostępnieniu ostatni obiekt w module.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Module::~Module, destruktor](../windows/module-tilde-module-destructor.md)|Deinicjuje bieżące wystąpienie **modułu** klasy.|

### <a name="protected-constructors"></a>Konstruktory chronione

|Nazwa|Opis|
|----------|-----------------|
|[Module::Module, konstruktor](../windows/module-module-constructor.md)|Inicjuje nowe wystąpienie klasy **modułu** klasy.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Module::Create, metoda](../windows/module-create-method.md)|Tworzy wystąpienie modułu.|
|[Module::DecrementObjectCount, metoda](../windows/module-decrementobjectcount-method.md)|Zmniejsza liczbę obiektów śledzonych przez moduł.|
|[Module::GetActivationFactory, metoda](../windows/module-getactivationfactory-method.md)|Pobiera fabrykę aktywacji dla modułu.|
|[Module::GetClassObject, metoda](../windows/module-getclassobject-method.md)|Retreives pamięci podręcznej fabryki klas.|
|[Module::GetModule, metoda](../windows/module-getmodule-method.md)|Tworzy wystąpienie modułu.|
|[Module::GetObjectCount, metoda](../windows/module-getobjectcount-method.md)|Pobiera liczbę obiektów zarządzanych przez ten moduł.|
|[Module::IncrementObjectCount, metoda](../windows/module-incrementobjectcount-method.md)|Zwiększa liczbę obiektów śledzonych przez moduł.|
|[Module::RegisterCOMObject, metoda](../windows/module-registercomobject-method.md)|Rejestruje jeden lub więcej obiektów COM, dzięki czemu inne aplikacje mogą łączyć się z nimi.|
|[Module::RegisterObjects, metoda](../windows/module-registerobjects-method.md)|Rejestruje obiekty COM lub środowiska wykonawczego Windows, dzięki czemu inne aplikacje mogą łączyć się z nimi.|
|[Module::RegisterWinRTObject, metoda](../windows/module-registerwinrtobject-method.md)|Rejestruje co najmniej jeden obiekt środowiska wykonawczego Windows, dzięki czemu inne aplikacje mogą łączyć się z nimi.|
|[Module::Terminate, metoda](../windows/module-terminate-method.md)|Powoduje, że wszystkie fabryki tworzone przez moduł, aby zamknąć.|
|[Module::UnregisterCOMObject, metoda](../windows/module-unregistercomobject-method.md)|Wyrejestrowuje jeden lub więcej obiektów COM, co uniemożliwia innych aplikacji na połączenie z nich.|
|[Module::UnregisterObjects, metoda](../windows/module-unregisterobjects-method.md)|Wyrejestrowuje obiektów w określonym module, tak aby inne aplikacje nie mogą nawiązać z nimi.|
|[Module::UnregisterWinRTObject, metoda](../windows/module-unregisterwinrtobject-method.md)|Wyrejestrowuje co najmniej jeden obiekt środowiska wykonawczego Windows, tak aby inne aplikacje nie mogą nawiązać z nimi.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[Module::Create, metoda](../windows/module-create-method.md)|Tworzy wystąpienie modułu.|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[Module::objectCount_, składowa danych](../windows/module-objectcount-data-member.md)|Przechowuje informacje o ile klasy zostały utworzone przy użyciu [wprowadzić](../windows/make-function.md) funkcji.|
|[Module::releaseNotifier_, składowa danych](../windows/module-releasenotifier-data-member.md)|Przechowuje wskaźnik do `ReleaseNotifier` obiektu.|

### <a name="macros"></a>Makra

|||
|-|-|
|[ActivatableClass](../windows/activatableclass-macros.md)|Wypełnia wewnętrzną pamięć podręczną zawierającą fabryki, który można utworzyć wystąpienie określonej klasy. To makro określa domyślne parametry identyfikator fabryki i grupy.|
|[ActivatableClassWithFactory](../windows/activatableclass-macros.md)|Wypełnia wewnętrzną pamięć podręczną zawierającą fabryki, który można utworzyć wystąpienie określonej klasy. To makro, można określić parametru określonego fabryki.|
|[ActivatableClassWithFactoryEx](../windows/activatableclass-macros.md)|Wypełnia wewnętrzną pamięć podręczną zawierającą fabryki, który można utworzyć wystąpienie określonej klasy. To makro umożliwia określenie konkretnego fabryki i parametry Identyfikatora grupy.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`ModuleBase`

`Module`

`Module`

## <a name="requirements"></a>Wymagania

**Nagłówek:** module.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL, przestrzeń nazw](../windows/microsoft-wrl-namespace.md)