---
title: Location — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- location
- CONCRT/concurrency::location
- CONCRT/concurrency::location::location
- CONCRT/concurrency::location::current
- CONCRT/concurrency::location::from_numa_node
dev_langs:
- C++
helpviewer_keywords:
- location class
ms.assetid: c3289f51-5bf1-4dff-a18d-d0dab8e5d9c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8c2352662de2d55be823064afd16354ff7f2c72e
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2018
ms.locfileid: "49163624"
---
# <a name="location-class"></a>location — Klasa

Abstrakcja fizycznej lokalizacji na sprzęcie.

## <a name="syntax"></a>Składnia

```
class location;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Lokalizacja](#ctor)|Przeciążone. Konstruuje `location` obiektu.|
|[~ location — destruktor](#dtor)|Niszczy `location` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[bieżący](#current)|Zwraca `location` obiekt reprezentujący miejscu bardziej konkretny od pozostałych, wykonywany jest wątek wywołujący.|
|[from_numa_node —](#from_numa_node)|Zwraca `location` obiekt, który reprezentuje dany Węzeł NUMA.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[operator!=](#operator_neq)|Określa, czy dwa `location` obiekty reprezentują inną lokalizację.|
|[operator=](#operator_eq)|Przypisuje zawartość innego `location` obiektu do wskazanego.|
|[operator==](#operator_eq_eq)|Określa, czy dwa `location` obiekty reprezentują tej samej lokalizacji.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`location`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrt.h

**Namespace:** współbieżności

##  <a name="dtor"></a> ~ lokalizacji

Niszczy `location` obiektu.

```
~location();
```

##  <a name="current"></a> bieżący

Zwraca `location` obiekt reprezentujący miejscu bardziej konkretny od pozostałych, wykonywany jest wątek wywołujący.

```
static location __cdecl current();
```

### <a name="return-value"></a>Wartość zwracana

Lokalizację reprezentujący bardziej konkretny od pozostałych miejscu wykonywanie wątku wywołującego.

##  <a name="from_numa_node"></a> from_numa_node —

Zwraca `location` obiekt, który reprezentuje dany Węzeł NUMA.

```
static location __cdecl from_numa_node(unsigned short _NumaNodeNumber);
```

### <a name="parameters"></a>Parametry

*_NumaNodeNumber*<br/>
Numer węzła NUMA do konstruowania lokalizację.

### <a name="return-value"></a>Wartość zwracana

Reprezentujący Węzeł NUMA, określone przez lokalizację `_NumaNodeNumber` parametru.

##  <a name="ctor"></a> Lokalizacja

Konstruuje `location` obiektu.

```
location();

location(
    const location& _Src);

location(
    T _LocationType,
    unsigned int _Id,
    unsigned int _BindingId = 0,
    _Inout_opt_ void* _PBinding = NULL);
```

### <a name="parameters"></a>Parametry

*_Src*<br/>

*_LocationType*<br/>

*_Identyfikator*<br/>

*_BindingId*<br/>

*_PBinding*<br/>
(Opcjonalnie) Wskaźnik powiązania.

### <a name="remarks"></a>Uwagi

Lokalizacja domyślne reprezentuje system jako całość.

##  <a name="operator_neq"></a> operator! =

Określa, czy dwa `location` obiekty reprezentują inną lokalizację.

```
bool operator!= (const location& _Rhs) const;
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Operand `location`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli dwiema lokalizacjami są różne, **false** inaczej.

##  <a name="operator_eq"></a> operator =

Przypisuje zawartość innego `location` obiektu do wskazanego.

```
location& operator= (const location& _Rhs);
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Źródło `location` obiektu.

### <a name="return-value"></a>Wartość zwracana

##  <a name="operator_eq_eq"></a> operator ==

Określa, czy dwa `location` obiekty reprezentują tej samej lokalizacji.

```
bool operator== (const location& _Rhs) const;
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Operand `location`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli dwiema lokalizacjami są identyczne, i **false** inaczej.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
