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
ms.openlocfilehash: c4bff519ea12646e94e92cde219fa38e4009a767
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38956460"
---
# <a name="rtsalloc-class"></a>rts_alloc — Klasa

Rts_alloc — klasa szablonu opisuje [filtru](../standard-library/allocators-header.md) zawierający tablicę pamięci podręcznej wystąpień i określa, które wystąpienie na potrzeby alokacji i dezalokacji w czasie wykonywania, a nie w czasie kompilacji.

## <a name="syntax"></a>Składnia

```cpp
template <class Cache>
class rts_alloc
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Cache*|Typ wystąpienia pamięci podręcznej znajdujących się w tablicy. Może to być [cache_chunklist — klasa](../standard-library/cache-chunklist-class.md), [cache_freelist](../standard-library/cache-freelist-class.md), lub [cache_suballoc](../standard-library/cache-suballoc-class.md).|

## <a name="remarks"></a>Uwagi

Tej klasy szablonu zawiera blok wiele wystąpień programu przydzielania i określa, które wystąpienie na potrzeby alokacji i dezalokacji w czasie wykonywania, a nie w czasie kompilacji. Kompilatory, których nie można skompilować ponowne wiązanie jest używany.

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[allocate](#allocate)|Przydziela blok pamięci.|
|[Cofnij Przydział](#deallocate)|Zwalnia określoną liczbę obiektów z pamięci masowej rozpoczynający się od określonej pozycji.|
|[equals](#equals)|Porównuje dwa pamięci podręczne dla równości.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<buforów >

**Namespace:** stdext

## <a name="allocate"></a>  rts_alloc::allocate

Przydziela blok pamięci.

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Liczba*|Liczba elementów w tablicy do przydzielenia.|

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do przydzielonego obiektu.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca `caches[_IDX].allocate(count)`, gdzie indeks `_IDX` zależy od rozmiaru żądanego bloku *liczba*, lub jeśli *liczba* jest za duży, funkcja zwraca `operator new(count)`. `cache`, która reprezentuje buforowany obiekt.

## <a name="deallocate"></a>  rts_alloc::deallocate

Zwalnia określoną liczbę obiektów z pamięci masowej rozpoczynający się od określonej pozycji.

```cpp
void deallocate(void* ptr, std::size_t count);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*ptr*|Wskaźnik do pierwszego obiektu można cofnąć przydziału z magazynu.|
|*Liczba*|Liczba obiektów, które można cofnąć przydziału z magazynu.|

### <a name="remarks"></a>Uwagi

Wywołania funkcji elementu członkowskiego `caches[_IDX].deallocate(ptr, count)`, gdzie indeks `_IDX` zależy od rozmiaru żądanego bloku *liczba*, lub jeśli *liczba* jest za duży, funkcja zwraca `operator delete(ptr)`.

## <a name="equals"></a>  rts_alloc::Equals

Porównuje dwa pamięci podręczne dla równości.

```cpp
bool equals(const sync<_Cache>& _Other) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*_Cache*|Buforowany obiekt skojarzony z filtrem.|
|*_Inne*|Buforowany obiekt do porównania dla równości.|

### <a name="remarks"></a>Uwagi

**wartość true,** Jeśli wynikiem `caches[0].equals(other.caches[0])`; w przeciwnym razie **false**. `caches` reprezentuje tablicę obiektów w pamięci podręcznej.

## <a name="see-also"></a>Zobacz także

[ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl)<br/>
[\<allocators — >](../standard-library/allocators-header.md)<br/>
