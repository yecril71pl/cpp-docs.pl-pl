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
ms.openlocfilehash: 4caf2cc2b6aa7494f343d10709f3190cb41631be
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232914"
---
# <a name="sync_none-class"></a>sync_none — Klasa

Opisuje [filtr synchronizacji](../standard-library/allocators-header.md) , który nie zapewnia synchronizacji.

## <a name="syntax"></a>Składnia

```cpp
template <class Cache>
class sync_none
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`Cache`|Typ pamięci podręcznej skojarzonej z filtrem synchronizacji. Może to być [cache_chunklist](../standard-library/cache-chunklist-class.md), [cache_freelist](../standard-library/cache-freelist-class.md)lub [cache_suballoc](../standard-library/cache-suballoc-class.md).|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[allocate](#allocate)|Przydziela blok pamięci.|
|[alokowany](#deallocate)|Zwalnia określoną liczbę obiektów z magazynu, zaczynając od określonej pozycji.|
|[równa się](#equals)|Porównuje dwie pamięci podręczne pod kątem równości.|

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<allocators>

**Przestrzeń nazw:** stdext

## <a name="sync_noneallocate"></a><a name="allocate"></a>sync_none:: Allocate

Przydziela blok pamięci.

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*liczbą*|Liczba elementów w tablicy, która ma zostać przypisana.|

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca `cache.allocate(count)` , gdzie `cache` jest obiektem pamięci podręcznej.

## <a name="sync_nonedeallocate"></a><a name="deallocate"></a>sync_none::d eallocate

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

Funkcja elementu członkowskiego wywołuje `cache.deallocate(ptr, count)` , gdzie `cache` reprezentuje obiekt pamięci podręcznej.

## <a name="sync_noneequals"></a><a name="equals"></a>sync_none:: Equals

Porównuje dwie pamięci podręczne pod kątem równości.

```cpp
bool equals(const sync<Cache>& Other) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Cache*|Obiekt pamięci podręcznej filtru synchronizacji.|
|*Inne problemy*|Obiekt pamięci podręcznej, który ma zostać porównany pod kątem równości.|

### <a name="return-value"></a>Wartość zwracana

Funkcja członkowska zawsze zwraca wartość **`true`** .

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz także

[\<allocators>](../standard-library/allocators-header.md)
