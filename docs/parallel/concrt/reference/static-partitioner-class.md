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
ms.openlocfilehash: 5120e3c53dc00ba9d5c3a4218efe1dcfb8f92e28
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57287648"
---
# <a name="staticpartitioner-class"></a>static_partitioner — Klasa

`static_partitioner` Klasa reprezentuje partycjonowania statycznego zakresu postanowiliśmy za pośrednictwem przez `parallel_for`. Partycjonera dzieli zakres na dowolną liczbę fragmentów są dostępne do harmonogramu underyling procesów roboczych.

## <a name="syntax"></a>Składnia

```
class static_partitioner;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[static_partitioner](#ctor)|Konstruuje `static_partitioner` obiektu.|
|[~static_partitioner Destructor](#dtor)|Niszczy `static_partitioner` obiektu.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`static_partitioner`

## <a name="requirements"></a>Wymagania

**Nagłówek:** ppl.h

**Namespace:** współbieżności

##  <a name="dtor"></a> ~ static_partitioner

Niszczy `static_partitioner` obiektu.

```
~static_partitioner();
```

##  <a name="ctor"></a> static_partitioner —

Konstruuje `static_partitioner` obiektu.

```
static_partitioner();
```

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
