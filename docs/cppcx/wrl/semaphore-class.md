---
title: Semaphore — Klasa
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Semaphore
- corewrappers/Microsoft::WRL::Wrappers::Semaphore::Lock
- corewrappers/Microsoft::WRL::Wrappers::Semaphore::operator=
- corewrappers/Microsoft::WRL::Wrappers::Semaphore::Semaphore
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Semaphore class
- Microsoft::WRL::Wrappers::Semaphore::Lock method
- Microsoft::WRL::Wrappers::Semaphore::operator= operator
- Microsoft::WRL::Wrappers::Semaphore::Semaphore, constructor
ms.assetid: ded53526-17b4-4381-9c60-ea5e77363db6
ms.openlocfilehash: 10357bb1cd46a33a8d4090c1ccc30050584d1816
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58787499"
---
# <a name="semaphore-class"></a>Semaphore — Klasa

Reprezentuje obiekt synchronizacji, który kontroluje zasobu udostępnionego, który może obsługiwać ograniczoną liczbę użytkowników.

## <a name="syntax"></a>Składnia

```cpp
class Semaphore : public HandleT<HandleTraits::SemaphoreTraits>;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

Nazwa       | Opis
---------- | ------------------------------------------------------
`SyncLock` | Synonim dla klasy, która obsługuje synchronicznej blokad.

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                               | Opis
---------------------------------- | ----------------------------------------------------
[Semaphore::Semaphore](#semaphore) | Inicjuje nowe wystąpienie klasy `Semaphore` klasy.

### <a name="public-methods"></a>Metody publiczne

Nazwa                     | Opis
------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------
[Semaphore::Lock](#lock) | Czeka, aż do bieżącego obiektu lub obiektów skojarzonych z określone dojście jest w stanie sygnałowego lub przed upływem określonego limitu czasu.

### <a name="public-operators"></a>Operatory publiczne

Nazwa                                     | Opis
---------------------------------------- | ---------------------------------------------------------------------------------------
[Semaphore::operator =](#operator-assign) | Przenosi określone dojście z `Semaphore` obiekt do bieżącego `Semaphore` obiektu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`Semaphore`

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Namespace:** Microsoft::wrl:: wrappers

## <a name="lock"></a>Semaphore::Lock

Czeka, aż do bieżącego obiektu lub `Semaphore` obiekt skojarzony z określone dojście jest w stanie sygnałowego lub przed upływem określonego limitu czasu.

```cpp
SyncLock Lock(
   DWORD milliseconds = INFINITE
);

static SyncLock Lock(
   HANDLE h,
   DWORD milliseconds = INFINITE
);
```

### <a name="parameters"></a>Parametry

*milliseconds*<br/>
Interwał limitu czasu w milisekundach. Wartość domyślna to NIESKOŃCZONE, który oczekuje w nieskończoność.

*h*<br/>
Dojście do `Semaphore` obiektu.

### <a name="return-value"></a>Wartość zwracana

A `Details::SyncLockWithStatusT<HandleTraits::SemaphoreTraits>`

## <a name="operator-assign"></a>Semaphore::operator =

Przenosi określone dojście z `Semaphore` obiekt do bieżącego `Semaphore` obiektu.

```cpp
Semaphore& operator=(
   _Inout_ Semaphore&& h
);
```

### <a name="parameters"></a>Parametry

*h*<br/>
Odwołania Rvalue do `Semaphore` obiektu.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do bieżącego `Semaphore` obiektu.

## <a name="semaphore"></a>Semaphore::Semaphore

Inicjuje nowe wystąpienie klasy `Semaphore` klasy.

```cpp
explicit Semaphore(
   HANDLE h
);

WRL_NOTHROW Semaphore(
   _Inout_ Semaphore&& h
);
```

### <a name="parameters"></a>Parametry

*h*<br/>
Dojście lub odwołanie rvalue, aby `Semaphore` obiektu.
