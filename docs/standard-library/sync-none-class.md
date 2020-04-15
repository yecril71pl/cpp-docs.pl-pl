---
title: sync_none — Klasa
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::sync_none
- allocators/stdext::sync_none::allocate
- allocators/stdext::sync_none::deallocate
- allocators/stdext::sync_none::equals
helpviewer_keywords:
- stdext::sync_none
- stdext::sync_none [C++], allocate
- stdext::sync_none [C++], deallocate
- stdext::sync_none [C++], equals
ms.assetid: f7473cee-14f3-4fe1-88bc-68cd085e59e1
ms.openlocfilehash: 046cbca30b6cdef2dc4e7dbbe2791d52384d9f25
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376570"
---
# <a name="sync_none-class"></a>sync_none — Klasa

W tym artykule opisano [filtr synchronizacji,](../standard-library/allocators-header.md) który nie zapewnia synchronizacji.

## <a name="syntax"></a>Składnia

```cpp
template <class Cache>
class sync_none
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`Cache`|Typ pamięci podręcznej skojarzonej z filtrem synchronizacji. Może to być [cache_chunklist,](../standard-library/cache-chunklist-class.md) [cache_freelist](../standard-library/cache-freelist-class.md)lub [cache_suballoc](../standard-library/cache-suballoc-class.md).|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[allocate](#allocate)|Przydziela blok pamięci.|
|[Deallocate](#deallocate)|Zwalnia określoną liczbę obiektów z magazynu, począwszy od określonej pozycji.|
|[equals](#equals)|Porównuje dwie pamięci podręczne dla równości.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<alokatory>

**Obszar nazw:** stdext

## <a name="sync_noneallocate"></a><a name="allocate"></a>sync_none::przydziel

Przydziela blok pamięci.

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Liczba*|Liczba elementów w tablicy, które mają zostać przydzielone.|

### <a name="remarks"></a>Uwagi

Funkcja elementu `cache.allocate(count)`członkowskiego `cache` zwraca , gdzie jest obiekt pamięci podręcznej.

## <a name="sync_nonedeallocate"></a><a name="deallocate"></a>sync_none::dlokalizuj

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

Wywołana przez `cache.deallocate(ptr, count)`funkcję `cache` elementu członkowskiego , gdzie reprezentuje obiekt pamięci podręcznej.

## <a name="sync_noneequals"></a><a name="equals"></a>sync_none::równa się

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

Funkcja elementu członkowskiego zawsze zwraca **wartość true**.

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[\<>alokatorów](../standard-library/allocators-header.md)
