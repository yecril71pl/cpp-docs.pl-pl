---
title: Module::MethodReleaseNotifier — Klasa
ms.date: 09/17/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::MethodReleaseNotifier
- module/Microsoft::WRL::Module::MethodReleaseNotifier::Invoke
- module/Microsoft::WRL::Module::MethodReleaseNotifier::method_
- module/Microsoft::WRL::Module::MethodReleaseNotifier::MethodReleaseNotifier
- module/Microsoft::WRL::Module::MethodReleaseNotifier::object_
helpviewer_keywords:
- Microsoft::WRL::Module::MethodReleaseNotifier class
- Microsoft::WRL::Module::MethodReleaseNotifier::Invoke method
- Microsoft::WRL::Module::MethodReleaseNotifier::method_ data member
- Microsoft::WRL::Module::MethodReleaseNotifier::MethodReleaseNotifier, constructor
- Microsoft::WRL::Module::MethodReleaseNotifier::object_ data member
ms.assetid: 5c2902be-964b-488f-9f1c-adf504995cbc
ms.openlocfilehash: c2b37073455f255eaea931e7aaedd1e34a14a104
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50469345"
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

*object*<br/>
Obiekt, którego funkcja członkowska jest program obsługi zdarzeń.

*— Metoda*<br/>
Funkcja elementu członkowskiego parametru *obiektu* oznacza to program obsługi zdarzeń.

*Wydania*<br/>
Określ **true** umożliwiające wywołanie bazowego [modułu:: ReleaseNotifier::Release()](../windows/module-releasenotifier-class.md#releasenotifier-release) metody; w przeciwnym razie określ **false**.

## <a name="methodreleasenotifier-object"></a>Module::methodreleasenotifier:: object_ —

Przechowuje wskaźnik do obiektu, którego funkcja członkowska jest program obsługi zdarzeń dla bieżącego `Module::MethodReleaseNotifier` obiektu.

```cpp
T* object_;
```
