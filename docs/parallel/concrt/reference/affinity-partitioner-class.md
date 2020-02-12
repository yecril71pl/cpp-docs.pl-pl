---
title: affinity_partitioner — Klasa
ms.date: 11/04/2016
f1_keywords:
- affinity_partitioner
- PPL/concurrency::affinity_partitioner
- PPL/concurrency::affinity_partitioner::affinity_partitioner
helpviewer_keywords:
- affinity_partitioner class
ms.assetid: 31bf7bb1-bd01-491c-9760-d9d60edfccad
ms.openlocfilehash: 0ae6bbee49d1b8873190a7054e55f65b40b31b13
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142872"
---
# <a name="affinity_partitioner-class"></a>affinity_partitioner — Klasa

Klasa `affinity_partitioner` jest podobna do klasy `static_partitioner`, ale zwiększa koligację pamięci podręcznej przez wybór zakresu mapowania na wątki robocze. Może znacząco poprawić wydajność, gdy pętla jest ponownie wykonywana nad tym samym zestawem danych, a dane pasują do pamięci podręcznej. Należy zauważyć, że ten sam obiekt `affinity_partitioner` musi być używany z kolejnymi iteracjami pętli równoległej, który jest wykonywany w określonym zestawie danych, aby można było korzystać z lokalizacji danych.

## <a name="syntax"></a>Składnia

```cpp
class affinity_partitioner;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[affinity_partitioner](#ctor)|Konstruuje obiekt `affinity_partitioner`.|
|[~ affinity_partitioner destruktor](#dtor)|Niszczy obiekt `affinity_partitioner`.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`affinity_partitioner`

## <a name="requirements"></a>Wymagania

**Nagłówek:** PPL. h

**Przestrzeń nazw:** współbieżność

## <a name="dtor"></a>~ affinity_partitioner

Niszczy obiekt `affinity_partitioner`.

```cpp
~affinity_partitioner();
```

## <a name="ctor"></a>affinity_partitioner

Konstruuje obiekt `affinity_partitioner`.

```cpp
affinity_partitioner();
```

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
