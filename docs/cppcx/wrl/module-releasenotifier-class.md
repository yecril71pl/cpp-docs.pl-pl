---
title: Module::ReleaseNotifier — Klasa
ms.date: 09/17/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::ReleaseNotifier
- module/Microsoft::WRL::Module::ReleaseNotifier::~ReleaseNotifier
- module/Microsoft::WRL::Module::ReleaseNotifier::Invoke
- module/Microsoft::WRL::Module::ReleaseNotifier::Release
- module/Microsoft::WRL::Module::ReleaseNotifier::ReleaseNotifier
helpviewer_keywords:
- Microsoft::WRL::Module::ReleaseNotifier class
- Microsoft::WRL::Module::ReleaseNotifier::~ReleaseNotifier, destructor
- Microsoft::WRL::Module::ReleaseNotifier::Invoke method
- Microsoft::WRL::Module::ReleaseNotifier::Release method
- Microsoft::WRL::Module::ReleaseNotifier::ReleaseNotifier, constructor
ms.assetid: 17249cd1-4d88-42e3-8146-da9e942d12bd
ms.openlocfilehash: f314d09c443d0d284e3a821b5c879bfb74baf812
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371275"
---
# <a name="modulereleasenotifier-class"></a>Module::ReleaseNotifier — Klasa

Wywołuje program obsługi zdarzeń po zwolnieniu ostatniego obiektu w module.

## <a name="syntax"></a>Składnia

```cpp
class ReleaseNotifier;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                                                                                | Opis
----------------------------------------------------------------------------------- | --------------------------------------------------------------------------
[Moduł::ReleaseNotifier::~ReleaseNotifier](#releasenotifier-tilde-releasenotifier) | Deinitializes bieżące wystąpienie `Module::ReleaseNotifier` klasy.
[Moduł::ReleaseNotifier::ReleaseNotifier](#releasenotifier-releasenotifier)        | Inicjuje nowe wystąpienie klasy `Module::ReleaseNotifier`.

### <a name="public-methods"></a>Metody publiczne

Nazwa                                                         | Opis
------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------
[Moduł::ReleaseNotifier::Wywołaj](#releasenotifier-invoke)   | Po zaimplementowaniu wywołuje program obsługi zdarzeń, gdy ostatni obiekt w module jest zwolniony.
[Module::ReleaseNotifier::Release](#releasenotifier-release) | Usuwa bieżący `Module::ReleaseNotifier` obiekt, jeśli obiekt został skonstruowany z parametrem **true**.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`ReleaseNotifier`

## <a name="requirements"></a>Wymagania

**Nagłówek:** module.h

**Obszar nazw:** Microsoft::WRL

## <a name="modulereleasenotifierreleasenotifier"></a><a name="releasenotifier-tilde-releasenotifier"></a>Moduł::ReleaseNotifier::~ReleaseNotifier

Deinitializes bieżące wystąpienie `Module::ReleaseNotifier` klasy.

```cpp
WRL_NOTHROW virtual ~ReleaseNotifier();
```

## <a name="modulereleasenotifierinvoke"></a><a name="releasenotifier-invoke"></a>Moduł::ReleaseNotifier::Wywołaj

Po zaimplementowaniu wywołuje program obsługi zdarzeń, gdy ostatni obiekt w module jest zwolniony.

```cpp
virtual void Invoke() = 0;
```

## <a name="modulereleasenotifierrelease"></a><a name="releasenotifier-release"></a>Moduł::ReleaseNotifier::Release

Usuwa bieżący `Module::ReleaseNotifier` obiekt, jeśli obiekt został skonstruowany z parametrem **true**.

```cpp
void Release() throw();
```

## <a name="modulereleasenotifierreleasenotifier"></a><a name="releasenotifier-releasenotifier"></a>Moduł::ReleaseNotifier::ReleaseNotifier

Inicjuje nowe wystąpienie klasy `Module::ReleaseNotifier`.

```cpp
ReleaseNotifier(bool release) throw();
```

### <a name="parameters"></a>Parametry

*Wydania*<br/>
`true`, aby usunąć `Release` to wystąpienie, gdy wywoływana jest metoda; `false` , aby nie usuwać tego wystąpienia.
