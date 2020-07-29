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
ms.openlocfilehash: 5b0e5766fda878acb1fdc54a79ce162444eb06de
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225725"
---
# <a name="modulemethodreleasenotifier-class"></a>Module::MethodReleaseNotifier — Klasa

Wywołuje program obsługi zdarzeń po wydaniu ostatniego obiektu w bieżącym module. Program obsługi zdarzeń jest określany przez obiekt i jego element członkowski typu wskaźnik-a-metoda.

## <a name="syntax"></a>Składnia

```cpp
template<typename T>
class MethodReleaseNotifier : public ReleaseNotifier;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ obiektu, którego funkcja członkowska jest programem obsługi zdarzeń.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                                                                                                 | Opis
---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------
[Module:: MethodReleaseNotifier:: MethodReleaseNotifier](#methodreleasenotifier-methodreleasenotifier) | Inicjuje nowe wystąpienie klasy `Module::MethodReleaseNotifier`.

### <a name="public-methods"></a>Metody publiczne

Nazwa                                                                   | Opis
---------------------------------------------------------------------- | -------------------------------------------------------------------------------------------
[Module:: MethodReleaseNotifier:: Invoke](#methodreleasenotifier-invoke) | Wywołuje procedurę obsługi zdarzeń skojarzoną z bieżącym `Module::MethodReleaseNotifier` obiektem.

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

Nazwa                                                                    | Opis
----------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------
[Module:: MethodReleaseNotifier:: method_](#methodreleasenotifier-method) | Przechowuje wskaźnik do programu obsługi zdarzeń dla bieżącego `Module::MethodReleaseNotifier` obiektu.
[Module:: MethodReleaseNotifier:: object_](#methodreleasenotifier-object) | Przechowuje wskaźnik do obiektu, którego funkcja członkowska jest programem obsługi zdarzeń dla bieżącego `Module::MethodReleaseNotifier` obiektu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`ReleaseNotifier`

`MethodReleaseNotifier`

## <a name="requirements"></a>Wymagania

**Nagłówek:** module. h

**Przestrzeń nazw:** Microsoft:: WRL

## <a name="modulemethodreleasenotifierinvoke"></a><a name="methodreleasenotifier-invoke"></a>Module:: MethodReleaseNotifier:: Invoke

Wywołuje procedurę obsługi zdarzeń skojarzoną z bieżącym `Module::MethodReleaseNotifier` obiektem.

```cpp
void Invoke();
```

## <a name="modulemethodreleasenotifiermethod_"></a><a name="methodreleasenotifier-method"></a>Module:: MethodReleaseNotifier:: method_

Przechowuje wskaźnik do programu obsługi zdarzeń dla bieżącego `Module::MethodReleaseNotifier` obiektu.

```cpp
void (T::* method_)();
```

## <a name="modulemethodreleasenotifiermethodreleasenotifier"></a><a name="methodreleasenotifier-methodreleasenotifier"></a>Module:: MethodReleaseNotifier:: MethodReleaseNotifier

Inicjuje nowe wystąpienie klasy `Module::MethodReleaseNotifier`.

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
Obiekt, którego funkcja członkowska jest programem obsługi zdarzeń.

*Method*<br/>
Funkcja członkowska *obiektu* parametru, który jest programem obsługi zdarzeń.

*Usuwanie*<br/>
Określ **`true`** , aby włączyć wywoływanie źródłowego [modułu:: ReleaseNotifier:: Release ()](module-releasenotifier-class.md#releasenotifier-release) ; w przeciwnym razie Określ **`false`** .

## <a name="modulemethodreleasenotifierobject_"></a><a name="methodreleasenotifier-object"></a>Module:: MethodReleaseNotifier:: object_

Przechowuje wskaźnik do obiektu, którego funkcja członkowska jest programem obsługi zdarzeń dla bieżącego `Module::MethodReleaseNotifier` obiektu.

```cpp
T* object_;
```
