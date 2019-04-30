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
ms.openlocfilehash: 2d8bbb8e8af17dd19953487c47e5fd40343fe349
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391091"
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
|[~auto_partitioner Destructor](#dtor)|Niszczy `auto_partitioner` obiektu.|

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

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
