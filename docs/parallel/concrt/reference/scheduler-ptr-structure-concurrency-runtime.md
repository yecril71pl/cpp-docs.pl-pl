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
ms.openlocfilehash: 60d71a26e5dffcadfb900ef15c26a6d9dc6d6f8b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358767"
---
# <a name="scheduler_ptr-structure"></a>Struktura scheduler_ptr

Reprezentuje wskaźnik do harmonogramu. Ta klasa istnieje, aby umożliwić specyfikacji wspólnego okresu istnienia przy użyciu shared_ptr lub tylko zwykły odniesienia przy użyciu surowego wskaźnika.

## <a name="syntax"></a>Składnia

```cpp
struct scheduler_ptr;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[scheduler_ptr::scheduler_ptr](#ctor)|Przeciążone. Tworzy wskaźnik harmonogramu od shared_ptr do harmonogramu|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[scheduler_ptr::get](#get)|Zwraca nieprzetworzony wskaźnik do harmonogramu|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[scheduler_ptr::operator bool](#operator_bool)|Sprawdź, czy wskaźnik harmonogramu nie jest zerowy|
|[scheduler_ptr::operator-&gt;](#operator_ptr)|Zachowywać się jak wskaźnik|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`scheduler_ptr`

## <a name="requirements"></a>Wymagania

**Nagłówek:** pplinterface.h

**Przestrzeń nazw:** współbieżność

## <a name="scheduler_ptrget-method"></a><a name="get"></a>scheduler_ptr::pobierz metodę

Zwraca nieprzetworzony wskaźnik do harmonogramu.

```cpp
scheduler_interface* get() const;
```

### <a name="return-value"></a>Wartość zwracana

## <a name="scheduler_ptroperator-bool"></a><a name="operator_bool"></a>scheduler_ptr::operator bool

Sprawdza, czy wskaźnik harmonogramu jest nie-null.

```cpp
operator bool() const;
```

## <a name="scheduler_ptroperator-gt"></a><a name="operator_ptr"></a>scheduler_ptr::operator-&gt;

Zachowuje się jak wskaźnik.

```cpp
scheduler_interface* operator->() const;
```

### <a name="return-value"></a>Wartość zwracana

## <a name="scheduler_ptrscheduler_ptr-constructor"></a><a name="ctor"></a>scheduler_ptr::scheduler_ptr konstruktor

Tworzy wskaźnik harmonogramu z shared_ptr do harmonogramu.

```cpp
explicit scheduler_ptr(std::shared_ptr<scheduler_interface> scheduler);
explicit scheduler_ptr(_In_opt_ scheduler_interface* pScheduler);
```

### <a name="parameters"></a>Parametry

*Harmonogram*<br/>
Harmonogram do konwersji.

*pScheduler ( pScheduler )*<br/>
Wskaźnik harmonogramu do konwersji.

## <a name="see-also"></a>Zobacz też

[współbieżność Obszar nazw](concurrency-namespace.md)
