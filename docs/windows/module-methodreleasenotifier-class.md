---
title: Module::MethodReleaseNotifier, klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/17/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::MethodReleaseNotifier
- module/Microsoft::WRL::Module::MethodReleaseNotifier::Invoke
- module/Microsoft::WRL::Module::MethodReleaseNotifier::method_
- module/Microsoft::WRL::Module::MethodReleaseNotifier::MethodReleaseNotifier
- module/Microsoft::WRL::Module::MethodReleaseNotifier::object_
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Module::MethodReleaseNotifier class
- Microsoft::WRL::Module::MethodReleaseNotifier::Invoke method
- Microsoft::WRL::Module::MethodReleaseNotifier::method_ data member
- Microsoft::WRL::Module::MethodReleaseNotifier::MethodReleaseNotifier, constructor
- Microsoft::WRL::Module::MethodReleaseNotifier::object_ data member
ms.assetid: 5c2902be-964b-488f-9f1c-adf504995cbc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8e78542e016ab0ba8ef33a5655b72fcdff45ccc4
ms.sourcegitcommit: 338e1ddc2f3869d92ba4b73599d35374cf1d5b69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/20/2018
ms.locfileid: "46494455"
---
# <a name="modulemethodreleasenotifier-class"></a>Module::MethodReleaseNotifier — Klasa

Wywołuje program obsługi zdarzeń po udostępnieniu ostatni obiekt w bieżącego modułu. Program obsługi zdarzeń jest określona przez obiekt i jego elementów członkowskich wskaźnika do metody.

## <a name="syntax"></a>Składnia

```cpp
template<typename T>
class MethodReleaseNotifier : public ReleaseNotifier;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ obiektu, którego funkcja członkowska jest program obsługi zdarzeń.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                                                                                                 | Opis
---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------
[Module::methodreleasenotifier:: methodreleasenotifier —](#methodreleasenotifier-methodreleasenotifier) | Inicjuje nowe wystąpienie klasy `Module::MethodReleaseNotifier` klasy.

### <a name="public-methods"></a>Metody publiczne

Nazwa                                                                   | Opis
---------------------------------------------------------------------- | -------------------------------------------------------------------------------------------
[Module::MethodReleaseNotifier:: Invoke](#methodreleasenotifier-invoke) | Wywołuje program obsługi zdarzeń skojarzonych z bieżącym `Module::MethodReleaseNotifier` obiektu.

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

Nazwa                                                                    | Opis
----------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------
[Module::methodreleasenotifier:: method_ —](#methodreleasenotifier-method) | Przechowuje wskaźnik do narzędzia obsługi zdarzeń dla bieżącego `Module::MethodReleaseNotifier` obiektu.
[Module::methodreleasenotifier:: object_ —](#methodreleasenotifier-object) | Przechowuje wskaźnik do obiektu, którego funkcja członkowska jest program obsługi zdarzeń dla bieżącego `Module::MethodReleaseNotifier` obiektu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`ReleaseNotifier`

`MethodReleaseNotifier`

## <a name="requirements"></a>Wymagania

**Nagłówek:** module.h

**Namespace:** Microsoft::WRL

## <a name="methodreleasenotifier-invoke"></a>Module::MethodReleaseNotifier:: Invoke

Wywołuje program obsługi zdarzeń skojarzonych z bieżącym `Module::MethodReleaseNotifier` obiektu.

```cpp
void Invoke();
```

## <a name="methodreleasenotifier-method"></a>Module::methodreleasenotifier:: method_ —

Przechowuje wskaźnik do narzędzia obsługi zdarzeń dla bieżącego `Module::MethodReleaseNotifier` obiektu.

```cpp
void (T::* method_)();
```

## <a name="methodreleasenotifier-methodreleasenotifier"></a>Module::methodreleasenotifier:: methodreleasenotifier —

Inicjuje nowe wystąpienie klasy `Module::MethodReleaseNotifier` klasy.

```cpp
MethodReleaseNotifier(
   _In_ T* object,
   _In_ void (T::* method)(),
   bool release) throw() :
            ReleaseNotifier(release), object_(object),
            method_(method);
```

### <a name="parameters"></a>Parametry

*object*  
Obiekt, którego funkcja członkowska jest program obsługi zdarzeń.

*— Metoda*  
Funkcja elementu członkowskiego parametru *obiektu* oznacza to program obsługi zdarzeń.

*Wydania*  
Określ `true` umożliwiające wywołanie bazowego [modułu:: ReleaseNotifier::Release()](../windows/module-releasenotifier-class.md#releasenotifier-release) metody; w przeciwnym razie określ `false`.

## <a name="methodreleasenotifier-object"></a>Module::methodreleasenotifier:: object_ —

Przechowuje wskaźnik do obiektu, którego funkcja członkowska jest program obsługi zdarzeń dla bieżącego `Module::MethodReleaseNotifier` obiektu.

```cpp
T* object_;
```
