---
title: Dispatchstate — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- DispatchState
- CONCRTRM/concurrency::DispatchState
- CONCRTRM/concurrency::DispatchState::DispatchState::DispatchState
- CONCRTRM/concurrency::DispatchState::DispatchState::m_dispatchStateSize
- CONCRTRM/concurrency::DispatchState::DispatchState::m_fIsPreviousContextAsynchronouslyBlocked
- CONCRTRM/concurrency::DispatchState::DispatchState::m_reserved
dev_langs:
- C++
helpviewer_keywords:
- DispatchState structure
ms.assetid: 8c52546e-1650-48a0-985f-7e4a0fc26a90
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2cb60a183497942d7a8bea6a333d2dea62d8e2b4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46448080"
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
