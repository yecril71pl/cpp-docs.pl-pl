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
ms.openlocfilehash: 2c4103f89f7fc74c5368bafac3c82685ff9b6e03
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372695"
---
# <a name="dispatchstate-structure"></a>DispatchState — Struktura

Struktura `DispatchState` jest używana do przenoszenia `IExecutionContext::Dispatch` stanu do metody. Opisuje okoliczności, w `Dispatch` których metoda jest wywoływana w interfejsie. `IExecutionContext`

## <a name="syntax"></a>Składnia

```cpp
struct DispatchState;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Stan wysyłki::Djednoczes](#ctor)|Konstruuje `DispatchState` nowy obiekt.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[Stan wysyłki::m_dispatchStateSize](#m_dispatchstatesize)|Rozmiar tej struktury, która jest używana do przechowywania wersji.|
|[Stan wysyłki::m_fIsPreviousContextAsynchronouslyBlocked](#m_fispreviouscontextasynchronouslyblocked)|Określa, czy ten kontekst `Dispatch` wszedł do metody, ponieważ poprzedni kontekst został zablokowany asynchronicznie. Jest to używane tylko w kontekście planowania usługi UMS i jest ustawiona na wartość `0` dla wszystkich innych kontekstów wykonywania.|
|[Stan wysyłki::m_reserved](#m_reserved)|Bity zarezerwowane dla przyszłych przekazywania informacji.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`DispatchState`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrtrm.h

**Przestrzeń nazw:** współbieżność

## <a name="dispatchstatedispatchstate-constructor"></a><a name="ctor"></a>Stan wysyłki::DispatchKonstruktor stanu

Konstruuje `DispatchState` nowy obiekt.

```cpp
DispatchState();
```

## <a name="dispatchstatem_dispatchstatesize-data-member"></a><a name="m_dispatchstatesize"></a>Stan wysyłki::m_dispatchStateSize element członkowski danych

Rozmiar tej struktury, która jest używana do przechowywania wersji.

```cpp
unsigned long m_dispatchStateSize;
```

## <a name="dispatchstatem_fispreviouscontextasynchronouslyblocked-data-member"></a><a name="m_fispreviouscontextasynchronouslyblocked"></a>Stan wysyłki::m_fIsPreviousContextAsynchronouslyBlocked element członkowski danych

Określa, czy ten kontekst `Dispatch` wszedł do metody, ponieważ poprzedni kontekst został zablokowany asynchronicznie. Jest to używane tylko w kontekście planowania usługi UMS i jest ustawiona na wartość `0` dla wszystkich innych kontekstów wykonywania.

```cpp
unsigned int m_fIsPreviousContextAsynchronouslyBlocked : 1;
```

## <a name="dispatchstatem_reserved-data-member"></a><a name="m_reserved"></a>Stan wysyłki::m_reserved element członkowski danych

Bity zarezerwowane dla przyszłych przekazywania informacji.

```cpp
unsigned int m_reserved : 31;
```

## <a name="see-also"></a>Zobacz też

[współbieżność Obszar nazw](concurrency-namespace.md)
