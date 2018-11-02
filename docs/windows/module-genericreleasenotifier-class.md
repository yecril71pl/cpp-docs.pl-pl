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
ms.openlocfilehash: c708dc101fde9d2631eca33ebe101f4aed421094
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50572357"
---
# <a name="modulegenericreleasenotifier-class"></a>Module::GenericReleaseNotifier — Klasa

Wywołuje program obsługi zdarzeń po udostępnieniu ostatni obiekt w bieżącego modułu. Program obsługi zdarzeń jest określone w lambda, funktor lub wskaźnik do funkcji.

## <a name="syntax"></a>Składnia

```cpp
template<typename T>
class GenericReleaseNotifier : public ReleaseNotifier;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ składowej danych, która zawiera lokalizację programu obsługi zdarzeń.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                                                                                                     | Opis
-------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------
[Module::genericreleasenotifier:: genericreleasenotifier —](#genericreleasenotifier-genericreleasenotifier) | Inicjuje nowe wystąpienie klasy `Module::GenericReleaseNotifier` klasy.

### <a name="public-methods"></a>Metody publiczne

Nazwa                                                                     | Opis
------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------
[Module::GenericReleaseNotifier:: Invoke](#genericreleasenotifier-invoke) | Wywołuje program obsługi zdarzeń skojarzonych z bieżącym `Module::GenericReleaseNotifier` obiektu.

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

Nazwa                                                                          | Opis
----------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------
[Module::genericreleasenotifier:: callback_ —](#genericreleasenotifier-callback) | Zawiera wyrażenie lambda, funktor lub obsługi zdarzeń wskaźnika do funkcji skojarzony z bieżącym `Module::GenericReleaseNotifier` obiektu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`ReleaseNotifier`

`GenericReleaseNotifier`

## <a name="requirements"></a>Wymagania

**Nagłówek:** module.h

**Namespace:** Microsoft::WRL

## <a name="genericreleasenotifier-callback"></a>Module::genericreleasenotifier:: callback_ —

Zawiera wyrażenie lambda, funktor lub obsługi zdarzeń wskaźnika do funkcji skojarzony z bieżącym `Module::GenericReleaseNotifier` obiektu.

```cpp
T callback_;
```

## <a name="genericreleasenotifier-genericreleasenotifier"></a>Module::genericreleasenotifier:: genericreleasenotifier —

Inicjuje nowe wystąpienie klasy `Module::GenericReleaseNotifier` klasy.

```cpp
GenericReleaseNotifier(
   T callback,
   bool release
) throw() : ReleaseNotifier(release), callback_(callback);
```

### <a name="parameters"></a>Parametry

*Wywołanie zwrotne*<br/>
Wyrażenie lambda, funktor lub program obsługi zdarzeń wskaźnika do funkcji, który może być wywoływany przy użyciu funkcji nawiasów (`()`).

*Wydania*<br/>
Określ **true** umożliwiające wywołanie bazowego [modułu:: ReleaseNotifier::Release()](../windows/module-releasenotifier-release.md) metody; w przeciwnym razie określ **false**.

## <a name="genericreleasenotifier-invoke"></a>Module::GenericReleaseNotifier:: Invoke

Wywołuje program obsługi zdarzeń skojarzonych z bieżącym `Module::GenericReleaseNotifier` obiektu.

```cpp
void Invoke();
```
