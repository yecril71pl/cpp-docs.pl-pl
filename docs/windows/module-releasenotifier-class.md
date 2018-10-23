---
title: Module::ReleaseNotifier, klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/17/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::ReleaseNotifier
- module/Microsoft::WRL::Module::ReleaseNotifier::~ReleaseNotifier
- module/Microsoft::WRL::Module::ReleaseNotifier::Invoke
- module/Microsoft::WRL::Module::ReleaseNotifier::Release
- module/Microsoft::WRL::Module::ReleaseNotifier::ReleaseNotifier
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Module::ReleaseNotifier class
- Microsoft::WRL::Module::ReleaseNotifier::~ReleaseNotifier, destructor
- Microsoft::WRL::Module::ReleaseNotifier::Invoke method
- Microsoft::WRL::Module::ReleaseNotifier::Release method
- Microsoft::WRL::Module::ReleaseNotifier::ReleaseNotifier, constructor
ms.assetid: 17249cd1-4d88-42e3-8146-da9e942d12bd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2128164fe3196a77991e755b865357e1aefcac23
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808488"
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
