---
title: rts_alloc — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- allocators/stdext::rts_alloc
- allocators/stdext::rts_alloc::allocate
- allocators/stdext::rts_alloc::deallocate
- allocators/stdext::rts_alloc::equals
dev_langs:
- C++
helpviewer_keywords:
- stdext::rts_alloc
- stdext::rts_alloc [C++], allocate
- stdext::rts_alloc [C++], deallocate
- stdext::rts_alloc [C++], equals
ms.assetid: ab41bffa-83d1-4a1c-87b9-5707d516931f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0f8bd1ec1436b960a0637a79cb04982a953636a6
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33856303"
---
# <a name="rtsalloc-class"></a>rts_alloc — Klasa

Rts_alloc — klasa szablonu opisuje [filtru](../standard-library/allocators-header.md) zawierający tablicę pamięci podręcznej wystąpienia i określa, które wystąpienie na potrzeby alokacji i dezalokacji w czasie wykonywania, a nie w czasie kompilacji.

## <a name="syntax"></a>Składnia

```cpp
template <class Cache>
class rts_alloc
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`Cache`|Typ wystąpienia pamięci podręcznej zawartych w tablicy. Może to być [cache_chunklist — klasa](../standard-library/cache-chunklist-class.md), [cache_freelist —](../standard-library/cache-freelist-class.md), lub [cache_suballoc —](../standard-library/cache-suballoc-class.md).|

## <a name="remarks"></a>Uwagi

Ta klasa szablonu zawiera blok wiele wystąpień programu przydzielania i określa, które wystąpienie na potrzeby alokacji lub dezalokacji w czasie wykonywania, a nie w czasie kompilacji. Jest ona używana z kompilatorów, których nie można skompilować ponownie Utwórz wiązanie.

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[allocate](#allocate)|Przydziela bloku pamięci.|
|[Cofnięcie przydziału](#deallocate)|Zwalnia określoną liczbę obiektów z magazynu rozpoczynający się od określonej pozycji.|
|[equals](#equals)|Porównuje dwa pamięci podręcznych pod kątem równości.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<allocators — >

**Namespace:** stdext —

## <a name="allocate"></a>  rts_alloc::allocate

Przydziela bloku pamięci.

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`count`|Liczba elementów w tablicy do przydzielenia.|

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do przydzielonego obiektu.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca `caches[_IDX].allocate(count)`, gdzie indeks `_IDX` jest zależny od rozmiaru żądanego bloku `count`, lub jeśli `count` jest zbyt duży, zwraca `operator new(count)`. `cache`, która reprezentuje buforowany obiekt.

## <a name="deallocate"></a>  rts_alloc::deallocate

Zwalnia określoną liczbę obiektów z magazynu rozpoczynający się od określonej pozycji.

```cpp
void deallocate(void* ptr, std::size_t count);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`ptr`|Wskaźnik do pierwszego obiektu do cofnięcia alokacji z magazynu.|
|`count`|Liczba obiektów do cofnięcia alokacji z magazynu.|

### <a name="remarks"></a>Uwagi

Wywołania funkcji Członkowskich `caches[_IDX].deallocate(ptr, count)`, gdzie indeks `_IDX` jest zależny od rozmiaru żądanego bloku `count`, lub jeśli `count` jest zbyt duży, zwraca `operator delete(ptr)`.

## <a name="equals"></a>  rts_alloc::Equals

Porównuje dwa pamięci podręcznych pod kątem równości.

```cpp
bool equals(const sync<_Cache>& _Other) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`_Cache`|Buforowany obiekt skojarzone z filtrem.|
|`_Other`|Buforowany obiekt do porównania równości.|

### <a name="remarks"></a>Uwagi

`true` Jeśli wynik `caches[0].equals(other.caches[0])`; w przeciwnym razie `false`. `caches` reprezentuje tablicę obiektów w pamięci podręcznej.

## <a name="see-also"></a>Zobacz także

[ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl)<br/>
[\<allocators — >](../standard-library/allocators-header.md)<br/>
