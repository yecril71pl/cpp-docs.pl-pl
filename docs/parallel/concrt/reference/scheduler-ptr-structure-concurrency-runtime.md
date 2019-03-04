---
title: scheduler_ptr, struktura
ms.date: 11/04/2016
f1_keywords:
- scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::get
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::operator bool
ms.assetid: e88c84af-c306-476d-aef1-f42a0fa0a80f
ms.openlocfilehash: 2373fe3bc8cac501d1b6b32ca66996eff47ba6f3
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57295048"
---
# <a name="schedulerptr-structure"></a>scheduler_ptr, struktura

Reprezentuje wskaźnik do harmonogramu. Ta klasa istnieje, aby zezwolić na specyfikację wspólnego okresu istnienia przy użyciu wskaźnika shared_ptr lub zwykłe odwołanie za pomocą wskaźnika raw.

## <a name="syntax"></a>Składnia

```
struct scheduler_ptr;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[scheduler_ptr::scheduler_ptr](#ctor)|Przeciążone. Tworzy wskaźnik harmonogramu z shared_ptr do harmonogramu|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[scheduler_ptr::get](#get)|Zwraca surowy wskaźnik do harmonogramu|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[scheduler_ptr::operator bool](#operator_bool)|Sprawdź, czy wskaźnik harmonogramu jest różna od null|
|[scheduler_ptr::operator-&gt;](#operator_ptr)|Zachowują się jak wskaźnik|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`scheduler_ptr`

## <a name="requirements"></a>Wymagania

**Nagłówek:** pplinterface.h

**Namespace:** współbieżności

##  <a name="get"></a>  scheduler_ptr::Get — metoda

Zwraca surowy wskaźnik do harmonogramu.

```
scheduler_interface* get() const;
```

### <a name="return-value"></a>Wartość zwracana

##  <a name="operator_bool"></a>  scheduler_ptr::operator bool

Sprawdza, czy wskaźnik harmonogramu jest różna od null.

```
operator bool() const;
```

##  <a name="operator_ptr"></a>  scheduler_ptr::operator-&gt;

Zachowuje się jak wskaźnik.

```
scheduler_interface* operator->() const;
```

### <a name="return-value"></a>Wartość zwracana

##  <a name="ctor"></a>  scheduler_ptr::scheduler_ptr — Konstruktor

Tworzy wskaźnik harmonogramu z shared_ptr do harmonogramu.

```
explicit scheduler_ptr(std::shared_ptr<scheduler_interface> scheduler);
explicit scheduler_ptr(_In_opt_ scheduler_interface* pScheduler);
```

### <a name="parameters"></a>Parametry

*scheduler*<br/>
Harmonogram do przekonwertowania.

*pScheduler*<br/>
Wskaźnik harmonogramu do przekonwertowania.

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
