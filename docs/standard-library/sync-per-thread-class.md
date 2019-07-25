---
title: sync_per_thread — Klasa
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::sync_per_thread
- allocators/stdext::sync_per_thread::allocate
- allocators/stdext::sync_per_thread::deallocate
- allocators/stdext::sync_per_thread::equals
helpviewer_keywords:
- stdext::sync_per_thread
- stdext::sync_per_thread [C++], allocate
- stdext::sync_per_thread [C++], deallocate
- stdext::sync_per_thread [C++], equals
ms.assetid: 47bf75f8-5b02-4760-b1d3-3099d08fe14c
ms.openlocfilehash: a08aa13aa46d5181e7c874b132b2bcbd5ec26dee
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450263"
---
# <a name="syncperthread-class"></a>sync_per_thread — Klasa

Opisuje [filtr synchronizacji](../standard-library/allocators-header.md) , który zawiera oddzielny obiekt pamięci podręcznej dla każdego wątku.

## <a name="syntax"></a>Składnia

```cpp
template <class Cache>
class sync_per_thread
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Pamięć podręczna*|Typ pamięci podręcznej skojarzonej z filtrem synchronizacji. Może to być [cache_chunklist](../standard-library/cache-chunklist-class.md), [cache_freelist](../standard-library/cache-freelist-class.md)lub [cache_suballoc](../standard-library/cache-suballoc-class.md).|

## <a name="remarks"></a>Uwagi

Przydziały korzystające `sync_per_thread` z programu mogą porównać wartość równą nawet wtedy, gdy bloki przydzielenia w jednym wątku nie mogą zostać cofnięte z innego wątku. Gdy użycie jednego z tych przydziałów pamięci przydzielanych w jednym wątku nie powinno być widoczne dla innych wątków. W tej rzeczywistości oznacza to, że kontener, który używa jednego z tych przystawek, powinien być dostępny tylko przez jeden wątek.

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[allocate](#allocate)|Przydziela blok pamięci.|
|[alokowany](#deallocate)|Zwalnia określoną liczbę obiektów z magazynu, zaczynając od określonej pozycji.|
|[equals](#equals)|Porównuje dwie pamięci podręczne pod kątem równości.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<przypisania >

**Przestrzeń nazw:** stdext

## <a name="allocate"></a>sync_per_thread:: Allocate

Przydziela blok pamięci.

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*liczbą*|Liczba elementów w tablicy, która ma zostać przypisana.|

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca wynik wywołania do `cache::allocate(count)` obiektu pamięci podręcznej należącego do bieżącego wątku. Jeśli żaden obiekt pamięci podręcznej nie został przydzielony do bieżącego wątku, najpierw przydzieli jeden.

## <a name="deallocate"></a>sync_per_thread::d eallocate

Zwalnia określoną liczbę obiektów z magazynu, zaczynając od określonej pozycji.

```cpp
void deallocate(void* ptr, std::size_t count);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*ptr*|Wskaźnik do pierwszego obiektu do cofnięcia przydziału z magazynu.|
|*liczbą*|Liczba obiektów do cofnięcia przydziału z magazynu.|

### <a name="remarks"></a>Uwagi

Funkcja członkowska wywołuje `deallocate` Obiekt pamięci podręcznej należący do bieżącego wątku. Jeśli żaden obiekt pamięci podręcznej nie został przydzielony do bieżącego wątku, najpierw przydzieli jeden.

## <a name="equals"></a>sync_per_thread:: Equals

Porównuje dwie pamięci podręczne pod kątem równości.

```cpp
bool equals(const sync<Cache>& Other) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Pamięć podręczna*|Obiekt pamięci podręcznej filtru synchronizacji.|
|*Inne*|Obiekt pamięci podręcznej, który ma zostać porównany pod kątem równości.|

### <a name="return-value"></a>Wartość zwracana

**wartość false** , jeśli nie przydzielono obiektu pamięci podręcznej dla tego obiektu lub dla *innych* w bieżącym wątku. W przeciwnym razie zwraca wynik zastosowania `operator==` do dwóch obiektów pamięci podręcznej.

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz także

[\<allocators>](../standard-library/allocators-header.md)
