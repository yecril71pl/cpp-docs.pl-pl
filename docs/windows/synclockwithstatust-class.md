---
title: Synclockwithstatust — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT
dev_langs:
- C++
helpviewer_keywords:
- SyncLockWithStatusT class
ms.assetid: 4832fd93-0ac8-4168-9404-b43fefea7476
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 69676651c77175b55f4363b525a3ca3acb9be46d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46437459"
---
# <a name="synclockwithstatust-class"></a>SyncLockWithStatusT — Klasa

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
template <
   typename SyncTraits
>
class SyncLockWithStatusT : public SyncLockT<SyncTraits>;
```

### <a name="parameters"></a>Parametry

*SyncTraits*<br/>
Typ, który może zająć wyłączne lub współużytkować własność zasobu.

## <a name="remarks"></a>Uwagi

Reprezentuje typ, który może zająć wyłączne lub współużytkować własność zasobu.

**Synclockwithstatust —** klasa jest używana do zaimplementowania [Mutex](../windows/mutex-class1.md) i [semafora](../windows/semaphore-class.md) klasy.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[SyncLockWithStatusT::SyncLockWithStatusT, konstruktor](../windows/synclockwithstatust-synclockwithstatust-constructor.md)|Inicjuje nowe wystąpienie klasy **synclockwithstatust —** klasy.|

### <a name="protected-constructors"></a>Konstruktory chronione

|Nazwa|Opis|
|----------|-----------------|
|[SyncLockWithStatusT::SyncLockWithStatusT, konstruktor](../windows/synclockwithstatust-synclockwithstatust-constructor.md)|Inicjuje nowe wystąpienie klasy **synclockwithstatust —** klasy.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[SyncLockWithStatusT::GetStatus, metoda](../windows/synclockwithstatust-getstatus-method.md)|Pobiera stan oczekiwania bieżącego **synclockwithstatust —** obiektu.|
|[SyncLockWithStatusT::IsLocked, metoda](../windows/synclockwithstatust-islocked-method.md)|Wskazuje, czy bieżący **synclockwithstatust —** obiekt posiada zasób; czyli, **synclockwithstatust —** obiekt jest *zablokowane*.|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[SyncLockWithStatusT::status_, składowa danych](../windows/synclockwithstatust-status-data-member.md)|Zawiera wynik podstawowych operacji oczekiwania po operacji blokadę na obiekcie na podstawie bieżącego **synclockwithstatust —** obiektu.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`SyncLockT`

`SyncLockWithStatusT`

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::Details

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL::Wrappers::Details, przestrzeń nazw](../windows/microsoft-wrl-wrappers-details-namespace.md)