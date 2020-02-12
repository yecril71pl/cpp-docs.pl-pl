---
title: simple_partitioner — Klasa
ms.date: 11/04/2016
f1_keywords:
- simple_partitioner
- PPL/concurrency::simple_partitioner
- PPL/concurrency::simple_partitioner::simple_partitioner
helpviewer_keywords:
- simple_partitioner class
ms.assetid: d7e997af-54d1-43f5-abe0-def72df6edb3
ms.openlocfilehash: 503f36b90c5eb3319f9aa2d56528172ffa95bb11
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142499"
---
# <a name="simple_partitioner-class"></a>simple_partitioner — Klasa

Klasa `simple_partitioner` reprezentuje statyczne partycjonowanie zakresu powtarzanego przez `parallel_for`. Program Partitioner dzieli zakres na fragmenty w taki sposób, że każdy fragment ma co najmniej liczbę iteracji określoną przez rozmiar fragmentu.

## <a name="syntax"></a>Składnia

```cpp
class simple_partitioner;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[simple_partitioner](#ctor)|Konstruuje obiekt `simple_partitioner`.|
|[~ simple_partitioner destruktor](#dtor)|Niszczy obiekt `simple_partitioner`.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`simple_partitioner`

## <a name="requirements"></a>Wymagania

**Nagłówek:** PPL. h

**Przestrzeń nazw:** współbieżność

## <a name="dtor"></a>~ simple_partitioner

Niszczy obiekt `simple_partitioner`.

```cpp
~simple_partitioner();
```

## <a name="ctor"></a>simple_partitioner

Konstruuje obiekt `simple_partitioner`.

```cpp
explicit simple_partitioner(_Size_type _Chunk_size);
```

### <a name="parameters"></a>Parametry

*_Chunk_size*<br/>
Minimalny rozmiar partycji.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
