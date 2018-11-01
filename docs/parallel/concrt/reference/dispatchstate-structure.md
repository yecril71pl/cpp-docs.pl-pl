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
ms.openlocfilehash: 4c15fc0ba9c78d8b6416cd88480c8ada6e3febf1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50603570"
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
|[Dispatchstate::dispatchstate —](#ctor)|Tworzy nowy `DispatchState` obiektu.|

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

##  <a name="ctor"></a>  Dispatchstate::dispatchstate — Konstruktor

Tworzy nowy `DispatchState` obiektu.

```
DispatchState();
```

##  <a name="m_dispatchstatesize"></a>  Dispatchstate::m_dispatchstatesize — członek danych

Rozmiar tej struktury, która jest używana do przechowywania wersji.

```
unsigned long m_dispatchStateSize;
```

##  <a name="m_fispreviouscontextasynchronouslyblocked"></a>  Dispatchstate::m_fispreviouscontextasynchronouslyblocked — członek danych

Informuje, czy wprowadzony w tym kontekście `Dispatch` metody, ponieważ poprzedni kontekst asynchronicznie zablokowany. To jest używane tylko w kontekście harmonogramu UMS i jest ustawiona na wartość `0` dla wszystkich kontekstów wykonanie.

```
unsigned int m_fIsPreviousContextAsynchronouslyBlocked : 1;
```

##  <a name="m_reserved"></a>  Dispatchstate::m_reserved — członek danych

Zarezerwowane dla przyszłych informacji przekazywanie usługi BITS.

```
unsigned int m_reserved : 31;
```

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
