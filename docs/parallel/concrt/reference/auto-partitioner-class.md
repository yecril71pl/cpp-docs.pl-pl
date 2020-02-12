---
title: auto_partitioner — Klasa
ms.date: 11/04/2016
f1_keywords:
- auto_partitioner
- PPL/concurrency::auto_partitioner
- PPL/concurrency::auto_partitioner::auto_partitioner
helpviewer_keywords:
- auto_partitioner class
ms.assetid: 7cc08e5d-20b4-47a4-b4b5-c214a78f5a9e
ms.openlocfilehash: 4d1d8f19069412240de8e9d69cdcfb34618f2796
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142863"
---
# <a name="auto_partitioner-class"></a>auto_partitioner — Klasa

Klasa `auto_partitioner` reprezentuje domyślną metodę `parallel_for`, `parallel_for_each` i `parallel_transform` użyć do partycjonowania zakresu, w którym się powtarza. Ta metoda partycjonowania wykorzystuje funkcję kradzieży zakresu na potrzeby równoważenia obciążenia, a także anulowania dla iteracji.

## <a name="syntax"></a>Składnia

```cpp
class auto_partitioner;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[auto_partitioner](#ctor)|Konstruuje obiekt `auto_partitioner`.|
|[~ auto_partitioner destruktor](#dtor)|Niszczy obiekt `auto_partitioner`.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`auto_partitioner`

## <a name="requirements"></a>Wymagania

**Nagłówek:** PPL. h

**Przestrzeń nazw:** współbieżność

## <a name="dtor"></a>~ auto_partitioner

Niszczy obiekt `auto_partitioner`.

```cpp
~auto_partitioner();
```

## <a name="ctor"></a>auto_partitioner

Konstruuje obiekt `auto_partitioner`.

```cpp
auto_partitioner();
```

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
