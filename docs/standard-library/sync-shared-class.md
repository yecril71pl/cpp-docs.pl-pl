---
title: sync_shared — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- allocators/stdext::sync_shared
- allocators/stdext::sync_shared::allocate
- allocators/stdext::sync_shared::deallocate
- allocators/stdext::sync_shared::equals
dev_langs:
- C++
helpviewer_keywords:
- stdext::sync_shared
- stdext::sync_shared [C++], allocate
- stdext::sync_shared [C++], deallocate
- stdext::sync_shared [C++], equals
ms.assetid: cab3af9e-3d1a-4f2c-8580-0f89e5687d8e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1e275bd195c11b605891b250e9264bad587eb853
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="syncshared-class"></a>sync_shared — Klasa

W tym artykule opisano [filtr synchronizacji](../standard-library/allocators-header.md) używający elementu mutex do kontrolowania dostępu do obiektu, który jest współużytkowana przez wszystkie allocators —.

## <a name="syntax"></a>Składnia

```cpp
template <class Cache>
class sync_shared
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`Cache`|Typ pamięci podręcznej skojarzone z filtrem synchronizacji. Może to być [cache_chunklist —](../standard-library/cache-chunklist-class.md), [cache_freelist —](../standard-library/cache-freelist-class.md), lub [cache_suballoc —](../standard-library/cache-suballoc-class.md).|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[allocate](#allocate)|Przydziela bloku pamięci.|
|[Cofnięcie przydziału](#deallocate)|Zwalnia określoną liczbę obiektów z magazynu rozpoczynający się od określonej pozycji.|
|[equals](#equals)|Porównuje dwa pamięci podręcznych pod kątem równości.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<allocators — >

**Namespace:** stdext —

## <a name="allocate"></a>  sync_shared::allocate

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

Funkcja członkowska blokady obiektu mutex, wywołania `cache.allocate(count)`odblokowuje obiektu mutex i zwraca wynik wywołania wcześniejszych `cache.allocate(count)`. `cache` reprezentuje bieżącego obiektu pamięci podręcznej.

## <a name="deallocate"></a>  sync_shared::deallocate

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

Ta funkcja członkowska blokady obiektu mutex, wywołania `cache.deallocate(ptr, count)`, gdzie `cache` reprezentuje obiektu pamięci podręcznej, a następnie odblokowuje obiektu mutex.

## <a name="equals"></a>  sync_shared::Equals

Porównuje dwa pamięci podręcznych pod kątem równości.

```cpp
bool equals(const sync_shared<Cache>& Other) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`Cache`|Typ pamięci podręcznej skojarzone z filtrem synchronizacji.|
|`Other`|Pamięć podręczna do porównania równości.|

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli wynik `cache.equals(Other.cache)`, gdzie `cache` reprezentuje obiektu pamięci podręcznej, jest `true`; w przeciwnym razie `false`.

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz także

[\<allocators — >](../standard-library/allocators-header.md)<br/>
