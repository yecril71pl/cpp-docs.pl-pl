---
title: Struktura scheduler_ptr | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::get
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::operator bool
dev_langs:
- C++
ms.assetid: e88c84af-c306-476d-aef1-f42a0fa0a80f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ea128a6122bf69735d118045eef2e8d8e323f8de
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46393422"
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

Zwraca surowy wskaźnik do harmonogramu

```
scheduler_interface* get() const;
```

### <a name="return-value"></a>Wartość zwracana

##  <a name="operator_bool"></a>  scheduler_ptr::operator bool

Sprawdź, czy wskaźnik harmonogramu jest różna od null

"" operator bool() const;
```

##  <a name="operator_ptr"></a>  scheduler_ptr::operator-&gt;

Behave like a pointer

```
scheduler_interface * — operator -> const;)
```

### Return Value

##  <a name="ctor"></a>  scheduler_ptr::scheduler_ptr Constructor

Creates a scheduler pointer from shared_ptr to scheduler

```
jawne scheduler_ptr (std::shared_ptr < scheduler_interface > harmonogramu);

jawne scheduler_ptr (_In_opt_ pScheduler scheduler_interface *);
```

### Parameters

*scheduler*<br/>
The scheduler to convert.

*pScheduler*<br/>
The scheduler pointer to convert.

## See Also

[concurrency Namespace](concurrency-namespace.md)
