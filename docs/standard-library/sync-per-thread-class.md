---
title: sync_per_thread — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- allocators/stdext::sync_per_thread
- allocators/stdext::sync_per_thread::allocate
- allocators/stdext::sync_per_thread::deallocate
- allocators/stdext::sync_per_thread::equals
dev_langs:
- C++
helpviewer_keywords:
- stdext::sync_per_thread
- stdext::sync_per_thread [C++], allocate
- stdext::sync_per_thread [C++], deallocate
- stdext::sync_per_thread [C++], equals
ms.assetid: 47bf75f8-5b02-4760-b1d3-3099d08fe14c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 956a18a477ca5a713f951da31ca276bc4e379727
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38964135"
---
# <a name="syncperthread-class"></a>sync_per_thread — Klasa

W tym artykule opisano [filtr synchronizacji](../standard-library/allocators-header.md) zapewniający obiektu pamięci podręcznej osobne dla każdego wątku.

## <a name="syntax"></a>Składnia

```cpp
template <class Cache>
class sync_per_thread
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Cache*|Typ pamięci podręcznej skojarzone z filtrem synchronizacji. Może to być [cache_chunklist](../standard-library/cache-chunklist-class.md), [cache_freelist](../standard-library/cache-freelist-class.md), lub [cache_suballoc](../standard-library/cache-suballoc-class.md).|

## <a name="remarks"></a>Uwagi

Buforów, które używają `sync_per_thread` można porównać taki sam, mimo że bloków alokowanych w jednym wątku nie można cofnąć przydziału z innego wątku. Gdy przy użyciu jednej z tych buforów bloki pamięci przydzielane w jednym wątku nie należy widoczne dla innych wątków. W praktyce oznacza to, że kontener, który korzysta z jednego z tych puli buforów powinna zostać oceniony jedynie przez pojedynczy wątek.

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[allocate](#allocate)|Przydziela blok pamięci.|
|[Cofnij Przydział](#deallocate)|Zwalnia określoną liczbę obiektów z pamięci masowej rozpoczynający się od określonej pozycji.|
|[equals](#equals)|Porównuje dwa pamięci podręczne dla równości.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<buforów >

**Namespace:** stdext

## <a name="allocate"></a>  sync_per_thread::allocate

Przydziela blok pamięci.

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Liczba*|Liczba elementów w tablicy do przydzielenia.|

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca wynik wywołania `cache::allocate(count)` obiektu pamięci podręcznej należące do bieżącego wątku. Jeśli żaden obiekt w pamięci podręcznej została przydzielona dla bieżącego wątku, najpierw przydziela jeden.

## <a name="deallocate"></a>  sync_per_thread::deallocate

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

Wywołania funkcji elementu członkowskiego `deallocate` obiektu pamięci podręcznej należące do bieżącego wątku. Jeśli żaden obiekt w pamięci podręcznej została przydzielona dla bieżącego wątku, najpierw przydziela jeden.

## <a name="equals"></a>  sync_per_thread::Equals

Porównuje dwa pamięci podręczne dla równości.

```cpp
bool equals(const sync<Cache>& Other) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Cache*|Buforowany obiekt filtr synchronizacji.|
|*Inne*|Buforowany obiekt do porównania dla równości.|

### <a name="return-value"></a>Wartość zwracana

**FALSE** Jeśli żaden obiekt w pamięci podręcznej została przydzielona dla tego obiektu lub *innych* w bieżącym wątku. W przeciwnym razie zwraca wynik zastosowania `operator==` do dwóch obiektów w pamięci podręcznej.

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz także

[\<allocators — >](../standard-library/allocators-header.md)<br/>
