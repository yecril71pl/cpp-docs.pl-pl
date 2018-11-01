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
ms.openlocfilehash: 5fc1b8965bf8bf2f86dd30f2195fa825f85f6d7e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50475910"
---
# <a name="modulereleasenotifier-class"></a>Module::ReleaseNotifier — Klasa

Wywołuje program obsługi zdarzeń po udostępnieniu ostatni obiekt w module.

## <a name="syntax"></a>Składnia

```cpp
class ReleaseNotifier;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                                                                                | Opis
----------------------------------------------------------------------------------- | --------------------------------------------------------------------------
[Module::ReleaseNotifier:: ~ ReleaseNotifier](#releasenotifier-tilde-releasenotifier) | Deinicjuje bieżące wystąpienie `Module::ReleaseNotifier` klasy.
[Module::releasenotifier:: releasenotifier —](#releasenotifier-releasenotifier)        | Inicjuje nowe wystąpienie klasy `Module::ReleaseNotifier` klasy.

### <a name="public-methods"></a>Metody publiczne

Nazwa                                                         | Opis
------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------
[Module::ReleaseNotifier:: Invoke](#releasenotifier-invoke)   | Po wdrożeniu, wywołuje program obsługi zdarzeń po udostępnieniu ostatni obiekt w module.
[Module::ReleaseNotifier::Release](#releasenotifier-release) | Usuwa bieżący `Module::ReleaseNotifier` obiektu, jeśli obiekt został zbudowany z parametrem **true**.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`ReleaseNotifier`

## <a name="requirements"></a>Wymagania

**Nagłówek:** module.h

**Namespace:** Microsoft::WRL

## <a name="releasenotifier-tilde-releasenotifier"></a>Module::ReleaseNotifier:: ~ ReleaseNotifier

Deinicjuje bieżące wystąpienie `Module::ReleaseNotifier` klasy.

```cpp
WRL_NOTHROW virtual ~ReleaseNotifier();
```

## <a name="releasenotifier-invoke"></a>Module::ReleaseNotifier:: Invoke

Po wdrożeniu, wywołuje program obsługi zdarzeń po udostępnieniu ostatni obiekt w module.

```cpp
virtual void Invoke() = 0;
```

## <a name="releasenotifier-release"></a>Module::ReleaseNotifier::Release

Usuwa bieżący `Module::ReleaseNotifier` obiektu, jeśli obiekt został zbudowany z parametrem **true**.

```cpp
void Release() throw();
```

## <a name="releasenotifier-releasenotifier"></a>Module::releasenotifier:: releasenotifier —

Inicjuje nowe wystąpienie klasy `Module::ReleaseNotifier` klasy.

```cpp
ReleaseNotifier(bool release) throw();
```

### <a name="parameters"></a>Parametry

*Wydania*<br/>
`true` Aby usunąć to wystąpienie kiedy `Release` wywoływana jest metoda; `false` nie należy usuwać tego wystąpienia.
