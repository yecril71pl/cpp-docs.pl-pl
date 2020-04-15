---
title: Mutex — Klasa
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Mutex
- corewrappers/Microsoft::WRL::Wrappers::Mutex::Lock
- corewrappers/Microsoft::WRL::Wrappers::Mutex::Mutex
- corewrappers/Microsoft::WRL::Wrappers::Mutex::operator=
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Mutex class
- Microsoft::WRL::Wrappers::Mutex::Lock method
- Microsoft::WRL::Wrappers::Mutex::Mutex, constructor
- Microsoft::WRL::Wrappers::Mutex::operator= operator
ms.assetid: 682a0963-721c-46a2-8871-000e9997505b
ms.openlocfilehash: 36466bd00c5b100f20ee87173e68fdef4131ec23
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371234"
---
# <a name="mutex-class"></a>Mutex — Klasa

Reprezentuje obiekt synchronizacji, który kontroluje wyłącznie zasób udostępniony.

## <a name="syntax"></a>Składnia

```cpp
class Mutex : public HandleT<HandleTraits::MutexTraits>;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne typedefs

Nazwa       | Opis
---------- | ------------------------------------------------------
`SyncLock` | Synonim dla klasy, która obsługuje blokady synchroniczne.

### <a name="public-constructor"></a>Konstruktor publiczny

Nazwa                   | Opis
---------------------- | ------------------------------------------------
[Mutex::Mutex](#mutex) | Inicjuje nowe wystąpienie klasy `Mutex`.

### <a name="public-members"></a>Członkowie publiczni

Nazwa                 | Opis
-------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------
[Mutex::Blokada](#lock) | Czeka, aż bieżący obiekt `Mutex` lub obiekt skojarzony z określonym uchwytem, zwalnia mutex lub upłynął określony interwał limit czasu.

### <a name="public-operator"></a>Operator publiczny

Nazwa                                 | Opis
------------------------------------ | ---------------------------------------------------------------------------
[Mutex::operator=](#operator-assign) | Przypisuje (przenosi) określony `Mutex` obiekt do `Mutex` bieżącego obiektu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`Mutex`

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Obszar nazw:** Microsoft::WRL::Otoki

## <a name="mutexlock"></a><a name="lock"></a>Mutex::Blokada

Czeka, aż bieżący obiekt `Mutex` lub obiekt skojarzony z określonym uchwytem, zwalnia mutex lub upłynął określony interwał limit czasu.

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
Dojście `Mutex` obiektu.

### <a name="return-value"></a>Wartość zwracana

## <a name="mutexmutex"></a><a name="mutex"></a>Mutex::Mutex

Inicjuje nowe wystąpienie klasy `Mutex`.

```cpp
explicit Mutex(
   HANDLE h
);

Mutex(
   _Inout_ Mutex&& h
);
```

### <a name="parameters"></a>Parametry

*H*<br/>
Dojście lub odwołanie rvalue do dojścia `Mutex` do obiektu.

### <a name="remarks"></a>Uwagi

Pierwszy konstruktor inicjuje `Mutex` obiekt z określonego dojścia. Drugi konstruktor inicjuje `Mutex` obiekt z określonego dojścia, a `Mutex` następnie przenosi własność obiektu mutex do bieżącego obiektu.

## <a name="mutexoperator"></a><a name="operator-assign"></a>Mutex::operator=

Przypisuje (przenosi) określony `Mutex` obiekt do `Mutex` bieżącego obiektu.

```cpp
Mutex& operator=(
   _Inout_ Mutex&& h
);
```

### <a name="parameters"></a>Parametry

*H*<br/>
Odwołanie do `Mutex` rvalue do obiektu.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do bieżącego `Mutex` obiektu.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz sekcję **Przenieś semantyki** [rvalue reference declarator: &&](../../cpp/rvalue-reference-declarator-amp-amp.md).
