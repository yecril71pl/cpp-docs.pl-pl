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
ms.openlocfilehash: dac25755c388e5297ce671da09b7938f09f1ef03
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57262795"
---
# <a name="affinitypartitioner-class"></a>affinity_partitioner — Klasa

`affinity_partitioner` Klasa jest podobna do `static_partitioner` klasy, ale zwiększa koligacji pamięci podręcznej przez siebie mapowania podzakresów na wątki robocze. Go może znacząco zwiększyć wydajność pętli jest ponownie wykonane przez tego samego zestawu danych, gdy dane są dopasowane do pamięci podręcznej. Należy pamiętać, że takie same `affinity_partitioner` obiektu musi być używany z kolejnych iteracjach pętli równoległej, który jest wykonywany dla określonego zestawu danych, aby korzystać z lokalizacja danych.

## <a name="syntax"></a>Składnia

```
class affinity_partitioner;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[affinity_partitioner](#ctor)|Konstruuje `affinity_partitioner` obiektu.|
|[~affinity_partitioner Destructor](#dtor)|Niszczy `affinity_partitioner` obiektu.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`affinity_partitioner`

## <a name="requirements"></a>Wymagania

**Nagłówek:** ppl.h

**Namespace:** współbieżności

##  <a name="dtor"></a> ~ affinity_partitioner

Niszczy `affinity_partitioner` obiektu.

```
~affinity_partitioner();
```

##  <a name="ctor"></a> affinity_partitioner —

Konstruuje `affinity_partitioner` obiektu.

```
affinity_partitioner();
```

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
