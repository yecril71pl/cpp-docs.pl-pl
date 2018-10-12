---
title: Synclockt — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::IsLocked
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::sync_
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::SyncLockT
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::~SyncLockT
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::Unlock
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Details::SyncLockT class
- Microsoft::WRL::Wrappers::Details::SyncLockT::IsLocked method
- Microsoft::WRL::Wrappers::Details::SyncLockT::sync_ data member
- Microsoft::WRL::Wrappers::Details::SyncLockT::SyncLockT, constructor
- Microsoft::WRL::Wrappers::Details::SyncLockT::~SyncLockT, destructor
- Microsoft::WRL::Wrappers::Details::SyncLockT::Unlock method
ms.assetid: a967f6f7-3555-43d1-b210-2bb65d63d15e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 66aa9c3a8ab0f5ae9fb5219b090ec5c9e3755203
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2018
ms.locfileid: "49162103"
---
# <a name="synclockt-class"></a>SyncLockT — Klasa

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
template <typename SyncTraits>
class SyncLockT;
```

### <a name="parameters"></a>Parametry

*SyncTraits*<br/>
Typ, który można przejmować na własność zasobu.

## <a name="remarks"></a>Uwagi

Reprezentuje typ, który może zająć wyłączne lub współużytkować własność zasobu.

`SyncLockT` Klasa jest używana, na przykład, pomagających w realizacji [SRWLock](../windows/srwlock-class.md) klasy.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                                      | Opis
----------------------------------------- | ----------------------------------------------------
[SyncLockT::SyncLockT](#synclockt)        | Inicjuje nowe wystąpienie klasy `SyncLockT` klasy.
[SyncLockT:: ~ SyncLockT](#tilde-synclockt) | Wyłącza wystąpienie `SyncLockT` klasy.

### <a name="protected-constructors"></a>Konstruktory chronione

Nazwa                               | Opis
---------------------------------- | ----------------------------------------------------
[SyncLockT::SyncLockT](#synclockt) | Inicjuje nowe wystąpienie klasy `SyncLockT` klasy.

### <a name="public-methods"></a>Metody publiczne

Nazwa                             | Opis
-------------------------------- | --------------------------------------------------------------------------------------------------------------
[SyncLockT::IsLocked](#islocked) | Wskazuje, czy bieżący `SyncLockT` obiekt posiada zasób; czyli, `SyncLockT` obiekt jest *zablokowane*.
[SyncLockT::Unlock](#unlock)     | Zwalnia kontrolę nad zasobów przechowywanych przez bieżącą `SyncLockT` obiektu, jeśli istnieje.

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

Nazwa                      | Opis
------------------------- | -------------------------------------------------------------------
[SyncLockT::sync_](#sync) | Przechowuje bazowego zasobu reprezentowanego przez `SyncLockT` klasy.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`SyncLockT`

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::Details

## <a name="tilde-synclockt"></a>SyncLockT:: ~ SyncLockT

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
~SyncLockT();
```

### <a name="remarks"></a>Uwagi

Wyłącza wystąpienie `SyncLockT` klasy.

Ten destruktor Odblokowano również bieżącą `SyncLockT` wystąpienia.

## <a name="islocked"></a>SyncLockT::IsLocked

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
bool IsLocked() const;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli `SyncLockT` obiektu jest zablokowany; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Wskazuje, czy bieżący `SyncLockT` obiekt posiada zasób; czyli, `SyncLockT` obiekt jest *zablokowane*.

## <a name="sync"></a>SyncLockT::sync_

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
typename SyncTraits::Type sync_;
```

### <a name="remarks"></a>Uwagi

Przechowuje bazowego zasobu reprezentowanego przez `SyncLockT` klasy.

## <a name="synclockt"></a>SyncLockT::SyncLockT

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
SyncLockT(
   _Inout_ SyncLockT&& other
);

explicit SyncLockT(
   typename SyncTraits::Type sync = SyncTraits::GetInvalidValue()  
);
```

### <a name="parameters"></a>Parametry

*other*<br/>
Odwołanie rvalue, do innego `SyncLockT` obiektu.

*sync*<br/>
Odwołanie do innego `SyncLockWithStatusT` obiektu.

### <a name="remarks"></a>Uwagi

Inicjuje nowe wystąpienie klasy `SyncLockT` klasy.

Pierwszy Konstruktor inicjuje bieżące `SyncLockT` obiektu z innego `SyncLockT` obiekt określony przez parametr *innych*, a następnie unieważnia innych `SyncLockT` obiektu. Drugi Konstruktor jest `protected`i inicjuje bieżące `SyncLockT` obiektu nieprawidłowym stanie.

## <a name="unlock"></a>SyncLockT::Unlock

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
void Unlock();
```

### <a name="remarks"></a>Uwagi

Zwalnia kontrolę nad zasobów przechowywanych przez bieżącą `SyncLockT` obiektu, jeśli istnieje.
