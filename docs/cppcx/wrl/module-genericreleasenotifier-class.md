---
title: Module::GenericReleaseNotifier — Klasa
ms.date: 09/17/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::GenericReleaseNotifier
- module/Microsoft::WRL::Module::GenericReleaseNotifier::callback_
- module/Microsoft::WRL::Module::GenericReleaseNotifier::GenericReleaseNotifier
- module/Microsoft::WRL::Module::GenericReleaseNotifier::Invoke
helpviewer_keywords:
- Microsoft::WRL::Module::GenericReleaseNotifier class
- Microsoft::WRL::Module::GenericReleaseNotifier::callback_ data member
- Microsoft::WRL::Module::GenericReleaseNotifier::GenericReleaseNotifier, constructor
- Microsoft::WRL::Module::GenericReleaseNotifier::Invoke method
ms.assetid: 244a8fbe-f89b-409b-aa65-db3e37f9b125
ms.openlocfilehash: e3cc8e33d596fb1d3ecc4a94fee7971a50ffe596
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371307"
---
# <a name="modulegenericreleasenotifier-class"></a>Module::GenericReleaseNotifier — Klasa

Wywołuje program obsługi zdarzeń, gdy ostatni obiekt w bieżącym module jest zwolniony. Program obsługi zdarzeń jest określony przez lambda, functor lub wskaźnik do funkcji.

## <a name="syntax"></a>Składnia

```cpp
template<typename T>
class GenericReleaseNotifier : public ReleaseNotifier;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ elementu członkowskiego danych, który zawiera lokalizację programu obsługi zdarzeń.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                                                                                                     | Opis
-------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------
[Moduł::GenericReleaseNotifier::GenericReleaseNotifier](#genericreleasenotifier-genericreleasenotifier) | Inicjuje nowe wystąpienie klasy `Module::GenericReleaseNotifier`.

### <a name="public-methods"></a>Metody publiczne

Nazwa                                                                     | Opis
------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------
[Moduł::GenericReleaseNotifier::Wywołaj](#genericreleasenotifier-invoke) | Wywołuje program obsługi zdarzeń skojarzony z bieżącym `Module::GenericReleaseNotifier` obiektem.

### <a name="protected-data-members"></a>Członkowie chronionych danych

Nazwa                                                                          | Opis
----------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------
[Moduł::GenericReleaseNotifier::callback_](#genericreleasenotifier-callback) | Przechowuje lambda, functor lub wskaźnik do funkcji obsługi zdarzeń `Module::GenericReleaseNotifier` skojarzonych z bieżącego obiektu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`ReleaseNotifier`

`GenericReleaseNotifier`

## <a name="requirements"></a>Wymagania

**Nagłówek:** module.h

**Obszar nazw:** Microsoft::WRL

## <a name="modulegenericreleasenotifiercallback_"></a><a name="genericreleasenotifier-callback"></a>Moduł::GenericReleaseNotifier::callback_

Przechowuje lambda, functor lub wskaźnik do funkcji obsługi zdarzeń `Module::GenericReleaseNotifier` skojarzonych z bieżącego obiektu.

```cpp
T callback_;
```

## <a name="modulegenericreleasenotifiergenericreleasenotifier"></a><a name="genericreleasenotifier-genericreleasenotifier"></a>Moduł::GenericReleaseNotifier::GenericReleaseNotifier

Inicjuje nowe wystąpienie klasy `Module::GenericReleaseNotifier`.

```cpp
GenericReleaseNotifier(
   T callback,
   bool release
) throw() : ReleaseNotifier(release), callback_(callback);
```

### <a name="parameters"></a>Parametry

*Wywołania zwrotnego*<br/>
Program obsługi zdarzeń lambda, functor lub wskaźnik do funkcji, który można wywołać`()`za pomocą operatora funkcji nawiasy ( ).

*Wydania*<br/>
Określ, `true` aby włączyć wywołanie podstawowej metody [modułu::ReleaseNotifier::Release();](module-releasenotifier-class.md#releasenotifier-release) w przeciwnym `false`razie należy określić .

## <a name="modulegenericreleasenotifierinvoke"></a><a name="genericreleasenotifier-invoke"></a>Moduł::GenericReleaseNotifier::Wywołaj

Wywołuje program obsługi zdarzeń skojarzony z bieżącym `Module::GenericReleaseNotifier` obiektem.

```cpp
void Invoke();
```
