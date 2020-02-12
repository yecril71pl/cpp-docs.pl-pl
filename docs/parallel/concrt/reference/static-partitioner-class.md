---
title: static_partitioner — Klasa
ms.date: 11/04/2016
f1_keywords:
- static_partitioner
- PPL/concurrency::static_partitioner
- PPL/concurrency::static_partitioner::static_partitioner
helpviewer_keywords:
- static_partitioner class
ms.assetid: 2b3dbdf0-6eb9-49f6-8639-03df1d974143
ms.openlocfilehash: 7a58daa27bc7a2f51f78a3068a2f152979ffdd72
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142677"
---
# <a name="static_partitioner-class"></a>static_partitioner — Klasa

Klasa `static_partitioner` reprezentuje statyczne partycjonowanie zakresu powtarzanego przez `parallel_for`. Partycja dzieli zakres na tyle fragmentów, ile jest dostępnych dla pracowników w źródłowym harmonogramie.

## <a name="syntax"></a>Składnia

```cpp
class static_partitioner;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[static_partitioner](#ctor)|Konstruuje obiekt `static_partitioner`.|
|[~ static_partitioner destruktor](#dtor)|Niszczy obiekt `static_partitioner`.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`static_partitioner`

## <a name="requirements"></a>Wymagania

**Nagłówek:** PPL. h

**Przestrzeń nazw:** współbieżność

## <a name="dtor"></a>~ static_partitioner

Niszczy obiekt `static_partitioner`.

```cpp
~static_partitioner();
```

## <a name="ctor"></a>static_partitioner

Konstruuje obiekt `static_partitioner`.

```cpp
static_partitioner();
```

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
