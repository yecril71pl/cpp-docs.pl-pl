---
title: rts_alloc — Klasa
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::rts_alloc
- allocators/stdext::rts_alloc::allocate
- allocators/stdext::rts_alloc::deallocate
- allocators/stdext::rts_alloc::equals
helpviewer_keywords:
- stdext::rts_alloc
- stdext::rts_alloc [C++], allocate
- stdext::rts_alloc [C++], deallocate
- stdext::rts_alloc [C++], equals
ms.assetid: ab41bffa-83d1-4a1c-87b9-5707d516931f
ms.openlocfilehash: f422b171c14695a1207a30419a10d50cdfb5adf0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228131"
---
# <a name="rts_alloc-class"></a>rts_alloc — Klasa

Szablon klasy rts_alloc opisuje [Filtr](../standard-library/allocators-header.md) , który przechowuje tablicę wystąpień pamięci podręcznej i określa, które wystąpienie ma być używane do alokacji i cofania alokacji w czasie wykonywania, a nie podczas kompilowania.

## <a name="syntax"></a>Składnia

```cpp
template <class Cache>
class rts_alloc
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Cache*|Typ wystąpień pamięci podręcznej zawartych w tablicy. Może to być [Cache_chunklist Class](../standard-library/cache-chunklist-class.md), [cache_freelist](../standard-library/cache-freelist-class.md)lub [cache_suballoc](../standard-library/cache-suballoc-class.md).|

## <a name="remarks"></a>Uwagi

Ten szablon klasy zawiera wiele wystąpień alokatora blokowego i określa, które wystąpienie ma być używane do alokacji lub cofania alokacji w czasie wykonywania, a nie podczas kompilowania. Jest on używany z kompilatorami, które nie mogą skompilować ponownie powiązania.

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[allocate](#allocate)|Przydziela blok pamięci.|
|[alokowany](#deallocate)|Zwalnia określoną liczbę obiektów z magazynu, zaczynając od określonej pozycji.|
|[równa się](#equals)|Porównuje dwie pamięci podręczne pod kątem równości.|

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<allocators>

**Przestrzeń nazw:** stdext

## <a name="rts_allocallocate"></a><a name="allocate"></a>rts_alloc:: Allocate

Przydziela blok pamięci.

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*liczbą*|Liczba elementów w tablicy, która ma zostać przypisana.|

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do przydzielony obiekt.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca `caches[_IDX].allocate(count)` , gdzie indeks `_IDX` jest określony przez żądaną *liczbę*rozmiarów bloku lub, jeśli *Liczba* jest zbyt duża, zwraca wartość `operator new(count)` . `cache`, która reprezentuje obiekt pamięci podręcznej.

## <a name="rts_allocdeallocate"></a><a name="deallocate"></a>rts_alloc::d eallocate

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

Funkcja elementu członkowskiego wywołuje `caches[_IDX].deallocate(ptr, count)` , gdzie indeks `_IDX` jest określony przez żądaną *liczbę*rozmiarów bloku lub, jeśli *Liczba* jest zbyt duża, zwraca `operator delete(ptr)` .

## <a name="rts_allocequals"></a><a name="equals"></a>rts_alloc:: Equals

Porównuje dwie pamięci podręczne pod kątem równości.

```cpp
bool equals(const sync<_Cache>& _Other) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*_Cache*|Obiekt pamięci podręcznej skojarzony z filtrem.|
|*_Other*|Obiekt pamięci podręcznej, który ma zostać porównany pod kątem równości.|

### <a name="remarks"></a>Uwagi

**`true`** Jeśli wynik `caches[0].equals(other.caches[0])` ; w przeciwnym razie, **`false`** . `caches`reprezentuje tablicę obiektów pamięci podręcznej.

## <a name="see-also"></a>Zobacz także

[ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl)\
[\<allocators>](../standard-library/allocators-header.md)
