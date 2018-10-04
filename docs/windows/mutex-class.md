---
title: Mutex — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Mutex
- corewrappers/Microsoft::WRL::Wrappers::Mutex::Lock
- corewrappers/Microsoft::WRL::Wrappers::Mutex::Mutex
- corewrappers/Microsoft::WRL::Wrappers::Mutex::operator=
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Mutex class
- Microsoft::WRL::Wrappers::Mutex::Lock method
- Microsoft::WRL::Wrappers::Mutex::Mutex, constructor
- Microsoft::WRL::Wrappers::Mutex::operator= operator
ms.assetid: 682a0963-721c-46a2-8871-000e9997505b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 37aaafa636f43671eb18436a49490caa10cf349f
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48789309"
---
# <a name="mutex-class"></a>Mutex — Klasa

Reprezentuje obiekt synchronizacji, który wyłącznie kontroluje zasobu udostępnionego.

## <a name="syntax"></a>Składnia

```cpp
class Mutex : public HandleT<HandleTraits::MutexTraits>;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

Nazwa       | Opis
---------- | ------------------------------------------------------
`SyncLock` | Synonim dla klasy, która obsługuje synchronicznej blokad.

### <a name="public-constructor"></a>Konstruktor publiczny

Nazwa                   | Opis
---------------------- | ------------------------------------------------
[Mutex::mutex —](#mutex) | Inicjuje nowe wystąpienie klasy `Mutex` klasy.

### <a name="public-members"></a>Publiczne elementy członkowskie

Nazwa                 | Opis
-------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------
[Mutex::Lock —](#lock) | Czeka, aż do bieżącego obiektu lub `Mutex` obiekt skojarzony z określonym dojściem wersji obiektu mutex lub określony limit czasu upłynął.

### <a name="public-operator"></a>Operator publiczny

Nazwa                                 | Opis
------------------------------------ | ---------------------------------------------------------------------------
[Mutex::operator =](#operator-assign) | Przypisuje (ruch) określonego `Mutex` obiekt do bieżącego `Mutex` obiektu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`Mutex`

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Namespace:** Microsoft::wrl:: wrappers

## <a name="lock"></a>Mutex::Lock —

Czeka, aż do bieżącego obiektu lub `Mutex` obiekt skojarzony z określonym dojściem wersji obiektu mutex lub określony limit czasu upłynął.

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

*MS*<br/>
Interwał limitu czasu w milisekundach. Wartość domyślna to NIESKOŃCZONE, który oczekuje w nieskończoność.

*h*<br/>
Dojście `Mutex` obiektu.

### <a name="return-value"></a>Wartość zwracana

## <a name="mutex"></a>Mutex::mutex —

Inicjuje nowe wystąpienie klasy `Mutex` klasy.

```cpp
explicit Mutex(
   HANDLE h
);

Mutex(
   _Inout_ Mutex&& h
);
```

### <a name="parameters"></a>Parametry

*h*<br/>
Dojście lub odwołanie rvalue do uchwytu, aby `Mutex` obiektu.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor inicjuje `Mutex` obiekt z określonego dojścia. Drugi Konstruktor inicjuje `Mutex` obiektu z określonego dojścia, a następnie przenosi własności obiektu mutex do bieżącego `Mutex` obiektu.

## <a name="operator-assign"></a>Mutex::operator =

Przypisuje (ruch) określonego `Mutex` obiekt do bieżącego `Mutex` obiektu.

```cpp
Mutex& operator=(
   _Inout_ Mutex&& h
);
```

### <a name="parameters"></a>Parametry

*h*<br/>
Odwołania rvalue do `Mutex` obiektu.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do bieżącego `Mutex` obiektu.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz **przenoszenie semantyki** części [Rvalue Reference Declarator: & &](../cpp/rvalue-reference-declarator-amp-amp.md).
