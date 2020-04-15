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
ms.openlocfilehash: c641f150b6f029facffa62f7b47c7da32138735e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371286"
---
# <a name="modulemethodreleasenotifier-class"></a>Module::MethodReleaseNotifier — Klasa

Wywołuje program obsługi zdarzeń, gdy ostatni obiekt w bieżącym module jest zwolniony. Program obsługi zdarzeń jest określony przez obiekt i jego element członkowski pointer-to-a-method.

## <a name="syntax"></a>Składnia

```cpp
template<typename T>
class MethodReleaseNotifier : public ReleaseNotifier;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ obiektu, którego funkcją elementu członkowskiego jest program obsługi zdarzeń.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                                                                                                 | Opis
---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------
[Moduł::MethodReleaseNotifier::MethodReleaseNotifier](#methodreleasenotifier-methodreleasenotifier) | Inicjuje nowe wystąpienie klasy `Module::MethodReleaseNotifier`.

### <a name="public-methods"></a>Metody publiczne

Nazwa                                                                   | Opis
---------------------------------------------------------------------- | -------------------------------------------------------------------------------------------
[Moduł::MethodReleaseNotifier::Wywołaj](#methodreleasenotifier-invoke) | Wywołuje program obsługi zdarzeń skojarzony z bieżącym `Module::MethodReleaseNotifier` obiektem.

### <a name="protected-data-members"></a>Członkowie chronionych danych

Nazwa                                                                    | Opis
----------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------
[Moduł::MethodReleaseNotifier::method_](#methodreleasenotifier-method) | Przechowuje wskaźnik do programu obsługi `Module::MethodReleaseNotifier` zdarzeń dla bieżącego obiektu.
[Moduł::MethodReleaseNotifier::object_](#methodreleasenotifier-object) | Przechowuje wskaźnik do obiektu, którego funkcja elementu `Module::MethodReleaseNotifier` członkowskiego jest program obsługi zdarzeń dla bieżącego obiektu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`ReleaseNotifier`

`MethodReleaseNotifier`

## <a name="requirements"></a>Wymagania

**Nagłówek:** module.h

**Obszar nazw:** Microsoft::WRL

## <a name="modulemethodreleasenotifierinvoke"></a><a name="methodreleasenotifier-invoke"></a>Moduł::MethodReleaseNotifier::Wywołaj

Wywołuje program obsługi zdarzeń skojarzony z bieżącym `Module::MethodReleaseNotifier` obiektem.

```cpp
void Invoke();
```

## <a name="modulemethodreleasenotifiermethod_"></a><a name="methodreleasenotifier-method"></a>Moduł::MethodReleaseNotifier::method_

Przechowuje wskaźnik do programu obsługi `Module::MethodReleaseNotifier` zdarzeń dla bieżącego obiektu.

```cpp
void (T::* method_)();
```

## <a name="modulemethodreleasenotifiermethodreleasenotifier"></a><a name="methodreleasenotifier-methodreleasenotifier"></a>Moduł::MethodReleaseNotifier::MethodReleaseNotifier

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

*obiekt*<br/>
Obiekt, którego funkcja elementu członkowskiego jest programem obsługi zdarzeń.

*Metoda*<br/>
Funkcja elementu członkowskiego *obiektu* parametru, który jest programem obsługi zdarzeń.

*Wydania*<br/>
Określ, `true` aby włączyć wywołanie podstawowej metody [modułu::ReleaseNotifier::Release();](module-releasenotifier-class.md#releasenotifier-release) w przeciwnym `false`razie należy określić .

## <a name="modulemethodreleasenotifierobject_"></a><a name="methodreleasenotifier-object"></a>Moduł::MethodReleaseNotifier::object_

Przechowuje wskaźnik do obiektu, którego funkcja elementu `Module::MethodReleaseNotifier` członkowskiego jest program obsługi zdarzeń dla bieżącego obiektu.

```cpp
T* object_;
```
