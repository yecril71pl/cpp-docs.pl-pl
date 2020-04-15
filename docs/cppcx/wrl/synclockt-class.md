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
ms.openlocfilehash: 52c4404fa28f680a9a7a4592d03f535e8406d1a4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374283"
---
# <a name="synclockt-class"></a>SyncLockT — Klasa

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

## <a name="syntax"></a>Składnia

```cpp
template <typename SyncTraits>
class SyncLockT;
```

### <a name="parameters"></a>Parametry

*SyncTraits (SyncTraits)*<br/>
Typ, który może przejąć na własność zasób.

## <a name="remarks"></a>Uwagi

Reprezentuje typ, który może przejąć wyłączną lub współwłasność zasobu.

Klasa `SyncLockT` jest używana, na przykład, aby pomóc w zaimplementowaniu [klasy SRWLock.](srwlock-class.md)

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                                      | Opis
----------------------------------------- | ----------------------------------------------------
[SyncLockT::SyncLockT](#synclockt)        | Inicjuje nowe wystąpienie klasy `SyncLockT`.
[SyncLockT::~SyncLockT](#tilde-synclockt) | Deinitializes wystąpienia `SyncLockT` klasy.

### <a name="protected-constructors"></a>Konstruktory chronione

Nazwa                               | Opis
---------------------------------- | ----------------------------------------------------
[SyncLockT::SyncLockT](#synclockt) | Inicjuje nowe wystąpienie klasy `SyncLockT`.

### <a name="public-methods"></a>Metody publiczne

Nazwa                             | Opis
-------------------------------- | --------------------------------------------------------------------------------------------------------------
[SyncLockT::Jest zablokowany](#islocked) | Wskazuje, czy `SyncLockT` bieżący obiekt jest właścicielem zasobu; oznacza to, `SyncLockT` że obiekt jest *zablokowany*.
[SyncLockT::Odblokuj](#unlock)     | Zwalnia kontrolę nad zasobem `SyncLockT` przechowywanym przez bieżący obiekt, jeśli istnieje.

### <a name="protected-data-members"></a>Członkowie chronionych danych

Nazwa                      | Opis
------------------------- | -------------------------------------------------------------------
[SyncLockT::sync_](#sync) | Przechowuje zasób bazowy reprezentowany przez `SyncLockT` klasę.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`SyncLockT`

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Obszar nazw:** Microsoft::WRL::Otoki::Details

## <a name="synclocktsynclockt"></a><a name="tilde-synclockt"></a>SyncLockT::~SyncLockT

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
~SyncLockT();
```

### <a name="remarks"></a>Uwagi

Deinitializes wystąpienia `SyncLockT` klasy.

Ten destruktor odblokowuje również bieżące `SyncLockT` wystąpienie.

## <a name="synclocktislocked"></a><a name="islocked"></a>SyncLockT::Jest zablokowany

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
bool IsLocked() const;
```

### <a name="return-value"></a>Wartość zwracana

**true,** `SyncLockT` jeśli obiekt jest zablokowany; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Wskazuje, czy `SyncLockT` bieżący obiekt jest właścicielem zasobu; oznacza to, `SyncLockT` że obiekt jest *zablokowany*.

## <a name="synclocktsync_"></a><a name="sync"></a>SyncLockT::sync_

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
typename SyncTraits::Type sync_;
```

### <a name="remarks"></a>Uwagi

Przechowuje zasób bazowy reprezentowany przez `SyncLockT` klasę.

## <a name="synclocktsynclockt"></a><a name="synclockt"></a>SyncLockT::SyncLockT

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
SyncLockT(
   _Inout_ SyncLockT&& other
);

explicit SyncLockT(
   typename SyncTraits::Type sync = SyncTraits::GetInvalidValue()
);
```

### <a name="parameters"></a>Parametry

*Innych*<br/>
Odwołanie rvalue do `SyncLockT` innego obiektu.

*synchronizacja*<br/>
Odwołanie do `SyncLockWithStatusT` innego obiektu.

### <a name="remarks"></a>Uwagi

Inicjuje nowe wystąpienie klasy `SyncLockT`.

Pierwszy `SyncLockT` konstruktor inicjuje bieżący obiekt z innego `SyncLockT` obiektu określonego przez parametr *inny*, a następnie unieważnia inny `SyncLockT` obiekt. Drugi konstruktor `protected`jest i inicjuje bieżący `SyncLockT` obiekt do nieprawidłowego stanu.

## <a name="synclocktunlock"></a><a name="unlock"></a>SyncLockT::Odblokuj

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
void Unlock();
```

### <a name="remarks"></a>Uwagi

Zwalnia kontrolę nad zasobem `SyncLockT` przechowywanym przez bieżący obiekt, jeśli istnieje.
