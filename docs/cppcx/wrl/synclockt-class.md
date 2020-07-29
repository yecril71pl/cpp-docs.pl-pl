---
title: SyncLockT — Klasa
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::IsLocked
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::sync_
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::SyncLockT
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::~SyncLockT
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::Unlock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Details::SyncLockT class
- Microsoft::WRL::Wrappers::Details::SyncLockT::IsLocked method
- Microsoft::WRL::Wrappers::Details::SyncLockT::sync_ data member
- Microsoft::WRL::Wrappers::Details::SyncLockT::SyncLockT, constructor
- Microsoft::WRL::Wrappers::Details::SyncLockT::~SyncLockT, destructor
- Microsoft::WRL::Wrappers::Details::SyncLockT::Unlock method
ms.assetid: a967f6f7-3555-43d1-b210-2bb65d63d15e
ms.openlocfilehash: 6a6e176020624f02e778ba5684a374abfbafa9e4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87184673"
---
# <a name="synclockt-class"></a>SyncLockT — Klasa

Obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
template <typename SyncTraits>
class SyncLockT;
```

### <a name="parameters"></a>Parametry

*SyncTraits*<br/>
Typ, który może przejąć własność zasobu.

## <a name="remarks"></a>Uwagi

Reprezentuje typ, który może przyjmować lub udostępniać prawa własności do zasobu.

`SyncLockT`Klasa jest używana, na przykład w celu ułatwienia implementacji klasy [SRWLock](srwlock-class.md) .

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                                      | Opis
----------------------------------------- | ----------------------------------------------------
[SyncLock:: SyncLock](#synclockt)        | Inicjuje nowe wystąpienie klasy `SyncLockT`.
[SyncLock:: ~ SyncLock](#tilde-synclockt) | Umożliwia odinicjowanie wystąpienia `SyncLockT` klasy.

### <a name="protected-constructors"></a>Konstruktory chronione

Nazwa                               | Opis
---------------------------------- | ----------------------------------------------------
[SyncLock:: SyncLock](#synclockt) | Inicjuje nowe wystąpienie klasy `SyncLockT`.

### <a name="public-methods"></a>Metody publiczne

Nazwa                             | Opis
-------------------------------- | --------------------------------------------------------------------------------------------------------------
[SyncLock:: IsLocked](#islocked) | Wskazuje, czy bieżący `SyncLockT` obiekt jest właścicielem zasobu, czyli `SyncLockT` obiekt jest *zablokowany*.
[SyncLock:: Unlock](#unlock)     | Zwalnia kontrolę nad zasobem przytrzymywanym przez bieżący `SyncLockT` obiekt, jeśli istnieje.

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

Nazwa                      | Opis
------------------------- | -------------------------------------------------------------------
[SyncLock:: sync_](#sync) | Przechowuje bazowego zasobu reprezentowanego przez `SyncLockT` klasę.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`SyncLockT`

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers. h

**Przestrzeń nazw:** Microsoft:: WRL:: otoki::D etails

## <a name="synclocktsynclockt"></a><a name="tilde-synclockt"></a>SyncLock:: ~ SyncLock

Obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
~SyncLockT();
```

### <a name="remarks"></a>Uwagi

Umożliwia odinicjowanie wystąpienia `SyncLockT` klasy.

Ten destruktor odblokowuje również bieżące `SyncLockT` wystąpienie.

## <a name="synclocktislocked"></a><a name="islocked"></a>SyncLock:: IsLocked

Obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
bool IsLocked() const;
```

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli `SyncLockT` obiekt jest zablokowany; w przeciwnym razie, **`false`** .

### <a name="remarks"></a>Uwagi

Wskazuje, czy bieżący `SyncLockT` obiekt jest właścicielem zasobu, czyli `SyncLockT` obiekt jest *zablokowany*.

## <a name="synclocktsync_"></a><a name="sync"></a>SyncLock:: sync_

Obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
typename SyncTraits::Type sync_;
```

### <a name="remarks"></a>Uwagi

Przechowuje bazowego zasobu reprezentowanego przez `SyncLockT` klasę.

## <a name="synclocktsynclockt"></a><a name="synclockt"></a>SyncLock:: SyncLock

Obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
SyncLockT(
   _Inout_ SyncLockT&& other
);

explicit SyncLockT(
   typename SyncTraits::Type sync = SyncTraits::GetInvalidValue()
);
```

### <a name="parameters"></a>Parametry

*różnych*<br/>
Rvalue odwołanie do innego `SyncLockT` obiektu.

*synchronizacji*<br/>
Odwołanie do innego `SyncLockWithStatusT` obiektu.

### <a name="remarks"></a>Uwagi

Inicjuje nowe wystąpienie klasy `SyncLockT`.

Pierwszy Konstruktor inicjuje bieżący `SyncLockT` obiekt z innego `SyncLockT` obiektu określonego przez parametr *inny*, a następnie unieważnia inny `SyncLockT` obiekt. Drugi Konstruktor jest **`protected`** i inicjuje bieżący `SyncLockT` obiekt w nieprawidłowym stanie.

## <a name="synclocktunlock"></a><a name="unlock"></a>SyncLock:: Unlock

Obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
void Unlock();
```

### <a name="remarks"></a>Uwagi

Zwalnia kontrolę nad zasobem przytrzymywanym przez bieżący `SyncLockT` obiekt, jeśli istnieje.
