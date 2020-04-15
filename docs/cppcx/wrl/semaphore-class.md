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
ms.openlocfilehash: e017b1b6316c4b6d49563d9a543950ab28961d90
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359357"
---
# <a name="semaphore-class"></a>Semaphore — Klasa

Reprezentuje obiekt synchronizacji, który steruje zasobem udostępnionym, który może obsługiwać ograniczoną liczbę użytkowników.

## <a name="syntax"></a>Składnia

```cpp
class Semaphore : public HandleT<HandleTraits::SemaphoreTraits>;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne typedefs

Nazwa       | Opis
---------- | ------------------------------------------------------
`SyncLock` | Synonim dla klasy, która obsługuje blokady synchroniczne.

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                               | Opis
---------------------------------- | ----------------------------------------------------
[Semafor::Semafor](#semaphore) | Inicjuje nowe wystąpienie klasy `Semaphore`.

### <a name="public-methods"></a>Metody publiczne

Nazwa                     | Opis
------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------
[Semafor::Blokada](#lock) | Oczekuje, aż bieżący obiekt lub obiekt skojarzony z określonym uchwytem znajduje się w stanie sygnału lub upłynął określony interwał limit czasu.

### <a name="public-operators"></a>Operatory publiczne

Nazwa                                     | Opis
---------------------------------------- | ---------------------------------------------------------------------------------------
[Semafor::operator=](#operator-assign) | Przenosi określony uchwyt `Semaphore` z obiektu `Semaphore` do bieżącego obiektu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`Semaphore`

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Obszar nazw:** Microsoft::WRL::Otoki

## <a name="semaphorelock"></a><a name="lock"></a>Semafor::Blokada

Oczekuje, aż bieżący obiekt `Semaphore` lub obiekt skojarzony z określonym uchwytem znajduje się w stanie sygnału lub upłynął określony interwał limit czasu.

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

*milisekundy*<br/>
Przedział limitów czasu w milisekundach. Wartością domyślną jest INFINITE, która czeka przez czas nieokreślony.

*H*<br/>
Dojście `Semaphore` do obiektu.

### <a name="return-value"></a>Wartość zwracana

Element `Details::SyncLockWithStatusT<HandleTraits::SemaphoreTraits>`.

## <a name="semaphoreoperator"></a><a name="operator-assign"></a>Semafor::operator=

Przenosi określony uchwyt `Semaphore` z obiektu `Semaphore` do bieżącego obiektu.

```cpp
Semaphore& operator=(
   _Inout_ Semaphore&& h
);
```

### <a name="parameters"></a>Parametry

*H*<br/>
Rvalue-odwołanie do `Semaphore` obiektu.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do bieżącego `Semaphore` obiektu.

## <a name="semaphoresemaphore"></a><a name="semaphore"></a>Semafor::Semafor

Inicjuje nowe wystąpienie klasy `Semaphore`.

```cpp
explicit Semaphore(
   HANDLE h
);

WRL_NOTHROW Semaphore(
   _Inout_ Semaphore&& h
);
```

### <a name="parameters"></a>Parametry

*H*<br/>
Dojście lub odwołanie rvalue `Semaphore` do obiektu.
