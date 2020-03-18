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
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418287"
---
# <a name="modulereleasenotifier-class"></a>Module::ReleaseNotifier — Klasa

Wywołuje program obsługi zdarzeń po wydaniu ostatniego obiektu w module.

## <a name="syntax"></a>Składnia

```cpp
class ReleaseNotifier;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

Name (Nazwa)                                                                                | Opis
----------------------------------------------------------------------------------- | --------------------------------------------------------------------------
[Module:: ReleaseNotifier:: ~ ReleaseNotifier](#releasenotifier-tilde-releasenotifier) | Deinicjalizuje bieżące wystąpienie klasy `Module::ReleaseNotifier`.
[Module:: ReleaseNotifier:: ReleaseNotifier](#releasenotifier-releasenotifier)        | Inicjuje nowe wystąpienie klasy `Module::ReleaseNotifier`.

### <a name="public-methods"></a>Metody publiczne

Name (Nazwa)                                                         | Opis
------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------
[Module:: ReleaseNotifier:: Invoke](#releasenotifier-invoke)   | Po zaimplementowaniu program wywołuje procedurę obsługi zdarzeń, gdy ostatni obiekt w module zostanie wydaną.
[Module::ReleaseNotifier::Release](#releasenotifier-release) | Usuwa bieżący obiekt `Module::ReleaseNotifier`, jeśli obiekt został skonstruowany przy użyciu parametru o **wartości true**.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`ReleaseNotifier`

## <a name="requirements"></a>Wymagania

**Nagłówek:** module. h

**Przestrzeń nazw:** Microsoft:: WRL

## <a name="releasenotifier-tilde-releasenotifier"></a>Module:: ReleaseNotifier:: ~ ReleaseNotifier

Deinicjalizuje bieżące wystąpienie klasy `Module::ReleaseNotifier`.

```cpp
WRL_NOTHROW virtual ~ReleaseNotifier();
```

## <a name="releasenotifier-invoke"></a>Module:: ReleaseNotifier:: Invoke

Po zaimplementowaniu program wywołuje procedurę obsługi zdarzeń, gdy ostatni obiekt w module zostanie wydaną.

```cpp
virtual void Invoke() = 0;
```

## <a name="releasenotifier-release"></a>Module:: ReleaseNotifier:: Release

Usuwa bieżący obiekt `Module::ReleaseNotifier`, jeśli obiekt został skonstruowany przy użyciu parametru o **wartości true**.

```cpp
void Release() throw();
```

## <a name="releasenotifier-releasenotifier"></a>Module:: ReleaseNotifier:: ReleaseNotifier

Inicjuje nowe wystąpienie klasy `Module::ReleaseNotifier`.

```cpp
ReleaseNotifier(bool release) throw();
```

### <a name="parameters"></a>Parametry

*Usuwanie*<br/>
`true`, aby usunąć to wystąpienie, gdy wywoływana jest metoda `Release`; nie `false` usunąć tego wystąpienia.
