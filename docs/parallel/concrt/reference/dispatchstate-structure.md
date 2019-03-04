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
ms.openlocfilehash: c755675a69ce86bc03a3fdb59fa7d43a20676495
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57265057"
---
# <a name="dispatchstate-structure"></a>DispatchState — Struktura

`DispatchState` Struktury służy do transferowania stan `IExecutionContext::Dispatch` metody. Zawiera opis sytuacji, w którym `Dispatch` wywoływana jest metoda `IExecutionContext` interfejsu.

## <a name="syntax"></a>Składnia

```
struct DispatchState;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[DispatchState::DispatchState](#ctor)|Tworzy nowy `DispatchState` obiektu.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[DispatchState::m_dispatchStateSize](#m_dispatchstatesize)|Rozmiar tej struktury, która jest używana do przechowywania wersji.|
|[DispatchState::m_fIsPreviousContextAsynchronouslyBlocked](#m_fispreviouscontextasynchronouslyblocked)|Informuje, czy wprowadzony w tym kontekście `Dispatch` metody, ponieważ poprzedni kontekst asynchronicznie zablokowany. To jest używane tylko w kontekście harmonogramu UMS i jest ustawiona na wartość `0` dla wszystkich kontekstów wykonanie.|
|[DispatchState::m_reserved](#m_reserved)|Zarezerwowane dla przyszłych informacji przekazywanie usługi BITS.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`DispatchState`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrtrm.h

**Namespace:** współbieżności

##  <a name="ctor"></a>  DispatchState::DispatchState Constructor

Tworzy nowy `DispatchState` obiektu.

```
DispatchState();
```

##  <a name="m_dispatchstatesize"></a>  DispatchState::m_dispatchStateSize Data Member

Rozmiar tej struktury, która jest używana do przechowywania wersji.

```
unsigned long m_dispatchStateSize;
```

##  <a name="m_fispreviouscontextasynchronouslyblocked"></a>  DispatchState::m_fIsPreviousContextAsynchronouslyBlocked Data Member

Informuje, czy wprowadzony w tym kontekście `Dispatch` metody, ponieważ poprzedni kontekst asynchronicznie zablokowany. To jest używane tylko w kontekście harmonogramu UMS i jest ustawiona na wartość `0` dla wszystkich kontekstów wykonanie.

```
unsigned int m_fIsPreviousContextAsynchronouslyBlocked : 1;
```

##  <a name="m_reserved"></a>  Dispatchstate::m_reserved — członek danych

Zarezerwowane dla przyszłych informacji przekazywanie usługi BITS.

```
unsigned int m_reserved : 31;
```

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
