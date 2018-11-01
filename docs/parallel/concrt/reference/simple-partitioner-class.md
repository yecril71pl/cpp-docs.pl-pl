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
ms.openlocfilehash: f3c5792a13d9e63a05ce6710dea77828f2510f0d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50522450"
---
# <a name="simplepartitioner-class"></a>simple_partitioner — Klasa

`simple_partitioner` Klasa reprezentuje partycjonowania statycznego zakresu postanowiliśmy za pośrednictwem przez `parallel_for`. Partycjonera dzieli zakres na fragmenty w taki sposób, że każdy fragment ma co najmniej liczba iteracji, określony przez rozmiar fragmentu.

## <a name="syntax"></a>Składnia

```
class simple_partitioner;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[simple_partitioner](#ctor)|Konstruuje `simple_partitioner` obiektu.|
|[~ simple_partitioner — destruktor](#dtor)|Niszczy `simple_partitioner` obiektu.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`simple_partitioner`

## <a name="requirements"></a>Wymagania

**Nagłówek:** ppl.h

**Namespace:** współbieżności

##  <a name="dtor"></a> ~ simple_partitioner

Niszczy `simple_partitioner` obiektu.

```
~simple_partitioner();
```

##  <a name="ctor"></a> simple_partitioner —

Konstruuje `simple_partitioner` obiektu.

```
explicit simple_partitioner(_Size_type _Chunk_size);
```

### <a name="parameters"></a>Parametry

*_Chunk_size*<br/>
Minimalny rozmiar partycji.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
