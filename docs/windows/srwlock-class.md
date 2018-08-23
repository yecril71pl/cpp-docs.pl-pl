---
title: Srwlock — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::SRWLock
dev_langs:
- C++
helpviewer_keywords:
- SRWLock class
ms.assetid: 4fa250e3-5f29-4b06-ac24-61b6c04ade93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fb97a29796c287cfaadddc305f25807de5dcba2e
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42604239"
---
# <a name="srwlock-class"></a>SRWLock — Klasa

Reprezentuje kieszeń czytnika/blokadę.

## <a name="syntax"></a>Składnia

```cpp
class SRWLock;
```

## <a name="remarks"></a>Uwagi

Cienki czytnika/blokadę służy do synchronizowania dostępu w wątkach do obiektu lub zasobu. Aby uzyskać więcej informacji, zobacz [funkcji synchronizacji](/windows/desktop/Sync/synchronization-functions).

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|||
|-|-|
|`SyncLockExclusive`|Synonim dla **SRWLock** obiekt, który jest uzyskiwany w trybie wyłączności.|
|`SyncLockShared`|Synonim dla **SRWLock** obiekt, który jest uzyskiwany w trybie udostępniania.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[SRWLock::SRWLock, konstruktor](../windows/srwlock-srwlock-constructor.md)|Inicjuje nowe wystąpienie klasy **SRWLock** klasy.|
|[SRWLock::~SRWLock, destruktor](../windows/srwlock-tilde-srwlock-destructor.md)|Wyłącza wystąpienie **SRWLock** klasy.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[SRWLock::LockExclusive, metoda](../windows/srwlock-lockexclusive-method.md)|Uzyskuje **SRWLock** obiektu w trybie wyłączności.|
|[SRWLock::LockShared, metoda](../windows/srwlock-lockshared-method.md)|Uzyskuje **SRWLock** obiektu w tryb udostępniania.|
|[SRWLock::TryLockExclusive, metoda](../windows/srwlock-trylockexclusive-method.md)|Próbuje pobrać **SRWLock** obiektu w trybie wyłączności dla bieżącej lub określonej **SRWLock** obiektu.|
|[SRWLock::TryLockShared, metoda](../windows/srwlock-trylockshared-method.md)|Próbuje pobrać **SRWLock** obiektu w tryb udostępniania dla bieżącej lub określonej **SRWLock** obiektu.|

### <a name="protected-data-member"></a>Element członkowski danych chronionych

|Nazwa|Opis|
|----------|-----------------|
|[SRWLock::SRWLock_, składowa danych](../windows/srwlock-srwlock-data-member.md)|Zawiera podstawowe zmienną blokady dla bieżącego **SRWLock** obiektu.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`SRWLock`

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Namespace:** Microsoft::wrl:: wrappers

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL::Wrappers, przestrzeń nazw](../windows/microsoft-wrl-wrappers-namespace.md)