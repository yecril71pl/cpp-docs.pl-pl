---
title: affinity_partitioner — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- affinity_partitioner
- PPL/concurrency::affinity_partitioner
- PPL/concurrency::affinity_partitioner::affinity_partitioner
dev_langs:
- C++
helpviewer_keywords:
- affinity_partitioner class
ms.assetid: 31bf7bb1-bd01-491c-9760-d9d60edfccad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9b1254b316a52bd3e61b3cafd81ba2e89ee88b62
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444648"
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
|[~ affinity_partitioner — destruktor](#dtor)|Niszczy `affinity_partitioner` obiektu.|

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

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
