---
title: Struktura scheduler_ptr
ms.date: 11/04/2016
f1_keywords:
- scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::get
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::operator bool
ms.assetid: e88c84af-c306-476d-aef1-f42a0fa0a80f
ms.openlocfilehash: fd044a6255a17882c26183223f71564f98c9f7b2
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142771"
---
# <a name="scheduler_ptr-structure"></a>Struktura scheduler_ptr

Reprezentuje wskaźnik do harmonogramu. Ta klasa istnieje, aby zezwolić na specyfikację wspólnego okresu istnienia przy użyciu shared_ptr lub tylko zwykłego odwołania przy użyciu wskaźnika RAW.

## <a name="syntax"></a>Składnia

```cpp
struct scheduler_ptr;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[scheduler_ptr:: scheduler_ptr](#ctor)|Przeciążone. Tworzy wskaźnik harmonogramu z shared_ptr do harmonogramu|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[scheduler_ptr:: Get](#get)|Zwraca surowy wskaźnik do harmonogramu|

### <a name="public-operators"></a>Operatory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[scheduler_ptr:: operator — bool](#operator_bool)|Sprawdź, czy wskaźnik harmonogramu ma wartość różną od null|
|[scheduler_ptr:: operator-&gt;](#operator_ptr)|Zachowuje się jak wskaźnik|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`scheduler_ptr`

## <a name="requirements"></a>Wymagania

**Nagłówek:** pplinterface. h

**Przestrzeń nazw:** współbieżność

## <a name="get"></a>scheduler_ptr:: Get — Metoda

Zwraca surowy wskaźnik do harmonogramu.

```cpp
scheduler_interface* get() const;
```

### <a name="return-value"></a>Wartość zwrócona

## <a name="operator_bool"></a>scheduler_ptr:: operator — bool

Testuje, czy wskaźnik harmonogramu jest inny niż null.

```cpp
operator bool() const;
```

## <a name="operator_ptr"></a>scheduler_ptr:: operator-&gt;

Zachowuje się jak wskaźnik.

```cpp
scheduler_interface* operator->() const;
```

### <a name="return-value"></a>Wartość zwrócona

## <a name="ctor"></a>scheduler_ptr:: scheduler_ptr, Konstruktor

Tworzy wskaźnik harmonogramu z shared_ptr do harmonogramu.

```cpp
explicit scheduler_ptr(std::shared_ptr<scheduler_interface> scheduler);
explicit scheduler_ptr(_In_opt_ scheduler_interface* pScheduler);
```

### <a name="parameters"></a>Parametry

*pracę*<br/>
Harmonogram do przekonwertowania.

*pScheduler*<br/>
Wskaźnik harmonogramu do przekonwertowania.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
