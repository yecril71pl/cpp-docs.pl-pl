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
ms.openlocfilehash: a0d06326b2ecbf3c427ae24b45751f7053778a0b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50500896"
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
|[~ static_partitioner — destruktor](#dtor)|Niszczy `static_partitioner` obiektu.|

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

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
