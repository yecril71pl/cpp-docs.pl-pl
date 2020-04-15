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
ms.openlocfilehash: 6ed84d906944a09fa355e281640e9480f3173554
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373424"
---
# <a name="rts_alloc-class"></a>rts_alloc — Klasa

Szablon klasy rts_alloc opisuje [filtr,](../standard-library/allocators-header.md) który zawiera tablicę wystąpień pamięci podręcznej i określa, które wystąpienie ma być używane do alokacji i alokacji w czasie wykonywania, a nie w czasie kompilacji.

## <a name="syntax"></a>Składnia

```cpp
template <class Cache>
class rts_alloc
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Pamięć podręczna*|Typ wystąpień pamięci podręcznej zawartych w tablicy. Może to być [klasa cache_chunklist,](../standard-library/cache-chunklist-class.md) [cache_freelist](../standard-library/cache-freelist-class.md)lub [cache_suballoc.](../standard-library/cache-suballoc-class.md)|

## <a name="remarks"></a>Uwagi

Ten szablon klasy zawiera wiele wystąpień alokatora bloków i określa, które wystąpienie ma być używane do alokacji lub alokacji transakcji w czasie wykonywania, a nie w czasie kompilacji. Jest on używany z kompilatorami, które nie można skompilować rebind.

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[allocate](#allocate)|Przydziela blok pamięci.|
|[Deallocate](#deallocate)|Zwalnia określoną liczbę obiektów z magazynu, począwszy od określonej pozycji.|
|[equals](#equals)|Porównuje dwie pamięci podręczne dla równości.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<alokatory>

**Obszar nazw:** stdext

## <a name="rts_allocallocate"></a><a name="allocate"></a>rts_alloc::przydziel

Przydziela blok pamięci.

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Liczba*|Liczba elementów w tablicy, które mają zostać przydzielone.|

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do przydzielonego obiektu.

### <a name="remarks"></a>Uwagi

Funkcja elementu `caches[_IDX].allocate(count)`członkowskiego zwraca `_IDX` , gdzie indeks jest określany przez żądaną *liczbę*rozmiarów `operator new(count)`bloku lub, jeśli *liczba* jest zbyt duża, zwraca . `cache`, który reprezentuje obiekt pamięci podręcznej.

## <a name="rts_allocdeallocate"></a><a name="deallocate"></a>rts_alloc::dlokalizuj

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

Funkcja elementu `caches[_IDX].deallocate(ptr, count)`członkowskiego wywołuje, `_IDX` gdzie indeks jest określany przez żądaną *liczbę*rozmiarów `operator delete(ptr)`bloku lub, jeśli *liczba* jest zbyt duża, zwraca .

## <a name="rts_allocequals"></a><a name="equals"></a>rts_alloc::równa się

Porównuje dwie pamięci podręczne dla równości.

```cpp
bool equals(const sync<_Cache>& _Other) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*_Cache*|Obiekt pamięci podręcznej skojarzony z filtrem.|
|*_Other*|Obiekt pamięci podręcznej do porównania dla równości.|

### <a name="remarks"></a>Uwagi

**prawda,** jeśli `caches[0].equals(other.caches[0])`wynik ; w przeciwnym razie **false**. `caches`reprezentuje tablicę obiektów pamięci podręcznej.

## <a name="see-also"></a>Zobacz też

[ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl)\
[\<>alokatorów](../standard-library/allocators-header.md)
