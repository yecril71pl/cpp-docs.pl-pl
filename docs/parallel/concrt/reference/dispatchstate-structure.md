---
title: DispatchState — Struktura
ms.date: 11/04/2016
f1_keywords:
- DispatchState
- CONCRTRM/concurrency::DispatchState
- CONCRTRM/concurrency::DispatchState::DispatchState::DispatchState
- CONCRTRM/concurrency::DispatchState::DispatchState::m_dispatchStateSize
- CONCRTRM/concurrency::DispatchState::DispatchState::m_fIsPreviousContextAsynchronouslyBlocked
- CONCRTRM/concurrency::DispatchState::DispatchState::m_reserved
helpviewer_keywords:
- DispatchState structure
ms.assetid: 8c52546e-1650-48a0-985f-7e4a0fc26a90
ms.openlocfilehash: 69e00893373ccca6e2ed676fbb7f5a109c49efdf
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143041"
---
# <a name="dispatchstate-structure"></a>DispatchState — Struktura

Struktura `DispatchState` jest używana do transferowania stanu do metody `IExecutionContext::Dispatch`. Opisano w nim sytuacje, w których Metoda `Dispatch` jest wywoływana w interfejsie `IExecutionContext`.

## <a name="syntax"></a>Składnia

```cpp
struct DispatchState;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[DispatchState::D ispatchState](#ctor)|Tworzy nowy obiekt `DispatchState`.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Name (Nazwa)|Opis|
|----------|-----------------|
|[DispatchState:: m_dispatchStateSize](#m_dispatchstatesize)|Rozmiar tej struktury, który jest używany do przechowywania wersji.|
|[DispatchState:: m_fIsPreviousContextAsynchronouslyBlocked](#m_fispreviouscontextasynchronouslyblocked)|Wskazuje, czy ten kontekst wprowadził metodę `Dispatch`, ponieważ poprzedni kontekst został zablokowany asynchronicznie. Jest on używany tylko w kontekście planowania UMS i ma ustawioną wartość `0` dla wszystkich innych kontekstów wykonania.|
|[DispatchState:: m_reserved](#m_reserved)|Bity zarezerwowane do przekazywania przyszłych informacji.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`DispatchState`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrtrm. h

**Przestrzeń nazw:** współbieżność

## <a name="ctor"></a>DispatchState::D Konstruktor ispatchState

Tworzy nowy obiekt `DispatchState`.

```cpp
DispatchState();
```

## <a name="m_dispatchstatesize"></a>Element członkowski danych DispatchState:: m_dispatchStateSize

Rozmiar tej struktury, który jest używany do przechowywania wersji.

```cpp
unsigned long m_dispatchStateSize;
```

## <a name="m_fispreviouscontextasynchronouslyblocked"></a>Element członkowski danych DispatchState:: m_fIsPreviousContextAsynchronouslyBlocked

Wskazuje, czy ten kontekst wprowadził metodę `Dispatch`, ponieważ poprzedni kontekst został zablokowany asynchronicznie. Jest on używany tylko w kontekście planowania UMS i ma ustawioną wartość `0` dla wszystkich innych kontekstów wykonania.

```cpp
unsigned int m_fIsPreviousContextAsynchronouslyBlocked : 1;
```

## <a name="m_reserved"></a>Element członkowski danych DispatchState:: m_reserved

Bity zarezerwowane do przekazywania przyszłych informacji.

```cpp
unsigned int m_reserved : 31;
```

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
