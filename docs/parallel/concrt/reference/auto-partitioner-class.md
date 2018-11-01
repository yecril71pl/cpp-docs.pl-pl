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
ms.openlocfilehash: 9e4701c39512613bd7525c2cc0e3d24a57e7689d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50644928"
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
