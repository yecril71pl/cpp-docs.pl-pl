---
title: auto_partitioner — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- auto_partitioner
- PPL/concurrency::auto_partitioner
- PPL/concurrency::auto_partitioner::auto_partitioner
dev_langs:
- C++
helpviewer_keywords:
- auto_partitioner class
ms.assetid: 7cc08e5d-20b4-47a4-b4b5-c214a78f5a9e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a2bb62d76733e77c2528a80dfc4e9ef358878895
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46425414"
---
# <a name="autopartitioner-class"></a>auto_partitioner — Klasa

`auto_partitioner` Klasa reprezentuje domyślną metodę `parallel_for`, `parallel_for_each` i `parallel_transform` służy do partycjonowania zakresu iteruje po nich. Ta metoda partycjonowania employes kradzież do równoważenia obciążenia w zakresie także na iteracji anulowania.

## <a name="syntax"></a>Składnia

```
class auto_partitioner;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[auto_partitioner](#ctor)|Konstruuje `auto_partitioner` obiektu.|
|[~ auto_partitioner — destruktor](#dtor)|Niszczy `auto_partitioner` obiektu.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`auto_partitioner`

## <a name="requirements"></a>Wymagania

**Nagłówek:** ppl.h

**Namespace:** współbieżności

##  <a name="dtor"></a> ~ auto_partitioner

Niszczy `auto_partitioner` obiektu.

```
~auto_partitioner();
```

##  <a name="ctor"></a> auto_partitioner —

Konstruuje `auto_partitioner` obiektu.

```
auto_partitioner();
```

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
