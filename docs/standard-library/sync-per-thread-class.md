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
ms.openlocfilehash: 2976cdc6671750f0da439e9eb42053518e4af8d9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376545"
---
# <a name="sync_per_thread-class"></a>sync_per_thread — Klasa

W tym artykule opisano [filtr synchronizacji,](../standard-library/allocators-header.md) który zapewnia oddzielny obiekt pamięci podręcznej dla każdego wątku.

## <a name="syntax"></a>Składnia

```cpp
template <class Cache>
class sync_per_thread
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Pamięć podręczna*|Typ pamięci podręcznej skojarzonej z filtrem synchronizacji. Może to być [cache_chunklist,](../standard-library/cache-chunklist-class.md) [cache_freelist](../standard-library/cache-freelist-class.md)lub [cache_suballoc](../standard-library/cache-suballoc-class.md).|

## <a name="remarks"></a>Uwagi

Alokatory, które `sync_per_thread` używają można porównać równe, nawet jeśli bloki przydzielone w jednym wątku nie można przydzielić z innego wątku. Podczas korzystania z jednego z tych bloków pamięci alokatorów przydzielonych w jednym wątku nie powinny być widoczne dla innych wątków. W praktyce oznacza to, że kontener, który używa jednego z tych alokatorów powinny być dostępne tylko przez jeden wątek.

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[allocate](#allocate)|Przydziela blok pamięci.|
|[Deallocate](#deallocate)|Zwalnia określoną liczbę obiektów z magazynu, począwszy od określonej pozycji.|
|[equals](#equals)|Porównuje dwie pamięci podręczne dla równości.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<alokatory>

**Obszar nazw:** stdext

## <a name="sync_per_threadallocate"></a><a name="allocate"></a>sync_per_thread::przydziel

Przydziela blok pamięci.

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Liczba*|Liczba elementów w tablicy, które mają zostać przydzielone.|

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca wynik `cache::allocate(count)` wywołania obiektu pamięci podręcznej należącego do bieżącego wątku. Jeśli żaden obiekt pamięci podręcznej nie został przydzielony dla bieżącego wątku, najpierw przydziela jeden.

## <a name="sync_per_threaddeallocate"></a><a name="deallocate"></a>sync_per_thread::dlokalizuj

Zwalnia określoną liczbę obiektów z magazynu, począwszy od określonej pozycji.

```cpp
void deallocate(void* ptr, std::size_t count);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Ptr*|Wskaźnik do pierwszego obiektu, który ma zostać cofnięty z magazynu.|
|*Liczba*|Liczba obiektów, które mają zostać przydzielone z magazynu.|

### <a name="remarks"></a>Uwagi

Funkcja elementu `deallocate` członkowskiego wywołuje obiekt pamięci podręcznej należący do bieżącego wątku. Jeśli żaden obiekt pamięci podręcznej nie został przydzielony dla bieżącego wątku, najpierw przydziela jeden.

## <a name="sync_per_threadequals"></a><a name="equals"></a>sync_per_thread::równa się

Porównuje dwie pamięci podręczne dla równości.

```cpp
bool equals(const sync<Cache>& Other) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Pamięć podręczna*|Obiekt pamięci podręcznej filtru synchronizacji.|
|*Inne*|Obiekt pamięci podręcznej do porównania dla równości.|

### <a name="return-value"></a>Wartość zwracana

**false,** jeśli nie obiekt pamięci podręcznej został przydzielony dla tego obiektu lub *innych* w bieżącym wątku. W przeciwnym razie zwraca `operator==` wynik zastosowania do dwóch obiektów pamięci podręcznej.

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[\<>alokatorów](../standard-library/allocators-header.md)
