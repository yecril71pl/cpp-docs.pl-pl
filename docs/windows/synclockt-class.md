---
title: Synclockt — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT
dev_langs:
- C++
helpviewer_keywords:
- SyncLockT class
ms.assetid: a967f6f7-3555-43d1-b210-2bb65d63d15e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d557b7ee6e6a0ae627ec7cc9a6b40b5b9dbb872c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46379570"
---
# <a name="synclockt-class"></a>SyncLockT — Klasa

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
template <
   typename SyncTraits
>
class SyncLockT;
```

### <a name="parameters"></a>Parametry

*SyncTraits*<br/>
Typ, który można przejmować na własność zasobu.

## <a name="remarks"></a>Uwagi

Reprezentuje typ, który może zająć wyłączne lub współużytkować własność zasobu.

**SyncLockT** klasa jest używana, na przykład, pomagających w realizacji [SRWLock](../windows/srwlock-class.md) klasy.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[SyncLockT::SyncLockT, konstruktor](../windows/synclockt-synclockt-constructor.md)|Inicjuje nowe wystąpienie klasy **SyncLockT** klasy.|
|[SyncLockT::~SyncLockT, destruktor](../windows/synclockt-tilde-synclockt-destructor.md)|Wyłącza wystąpienie **SyncLockT** klasy.|

### <a name="protected-constructors"></a>Konstruktory chronione

|Nazwa|Opis|
|----------|-----------------|
|[SyncLockT::SyncLockT, konstruktor](../windows/synclockt-synclockt-constructor.md)|Inicjuje nowe wystąpienie klasy **SyncLockT** klasy.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[SyncLockT::IsLocked, metoda](../windows/synclockt-islocked-method.md)|Wskazuje, czy bieżący **SyncLockT** obiekt posiada zasób; czyli, **SyncLockT** obiekt jest *zablokowane*.|
|[SyncLockT::Unlock, metoda](../windows/synclockt-unlock-method.md)|Zwalnia kontrolę nad zasobów przechowywanych przez bieżącą **SyncLockT** obiektu, jeśli istnieje.|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[SyncLockT::sync_, składowa danych](../windows/synclockt-sync-data-member.md)|Przechowuje bazowego zasobu reprezentowanego przez **SyncLockT** klasy.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`SyncLockT`

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::Details

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL::Wrappers::Details, przestrzeń nazw](../windows/microsoft-wrl-wrappers-details-namespace.md)<br/>
[SRWLock, klasa](../windows/srwlock-class.md)