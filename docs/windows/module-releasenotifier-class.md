---
title: Module::ReleaseNotifier, klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::ReleaseNotifier
dev_langs:
- C++
helpviewer_keywords:
- ReleaseNotifier class
ms.assetid: 17249cd1-4d88-42e3-8146-da9e942d12bd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e6f720d0a918a22aee4a4cade6af1cb02a90e8d8
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42588872"
---
# <a name="modulereleasenotifier-class"></a>Module::ReleaseNotifier — Klasa

Wywołuje program obsługi zdarzeń po udostępnieniu ostatni obiekt w module.

## <a name="syntax"></a>Składnia

```cpp
class ReleaseNotifier;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Module::ReleaseNotifier::~ReleaseNotifier, destruktor](../windows/module-releasenotifier-tilde-releasenotifier-destructor.md)|Deinicjuje bieżące wystąpienie **Module::ReleaseNotifier** klasy.|
|[Module::ReleaseNotifier::ReleaseNotifier, konstruktor](../windows/module-releasenotifier-releasenotifier-constructor.md)|Inicjuje nowe wystąpienie klasy **Module::ReleaseNotifier** klasy.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Module::ReleaseNotifier::Invoke, metoda](../windows/module-releasenotifier-invoke-method.md)|Po wdrożeniu, wywołuje program obsługi zdarzeń po udostępnieniu ostatni obiekt w module.|
|[Module::ReleaseNotifier::Release](../windows/module-releasenotifier-release.md)|Usuwa bieżący **Module::ReleaseNotifier** obiektu, jeśli obiekt został zbudowany z parametrem **true**.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`ReleaseNotifier`

## <a name="requirements"></a>Wymagania

**Nagłówek:** module.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też
[Klasa modułu](../windows/module-class.md)