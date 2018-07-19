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
ms.openlocfilehash: 0fb9b61ec4d2abc6ae73b2ebed7571398857d517
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38963462"
---
# <a name="syncshared-class"></a>sync_shared — Klasa

W tym artykule opisano [filtr synchronizacji](../standard-library/allocators-header.md) używającej elementu mutex do kontrolowania dostępu do obiektu pamięci podręcznej, który jest współużytkowany przez wszystkich buforów.

## <a name="syntax"></a>Składnia

```cpp
template <class Cache>
class sync_shared
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Cache*|Typ pamięci podręcznej skojarzone z filtrem synchronizacji. Może to być [cache_chunklist](../standard-library/cache-chunklist-class.md), [cache_freelist](../standard-library/cache-freelist-class.md), lub [cache_suballoc](../standard-library/cache-suballoc-class.md).|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[allocate](#allocate)|Przydziela blok pamięci.|
|[Cofnij Przydział](#deallocate)|Zwalnia określoną liczbę obiektów z pamięci masowej rozpoczynający się od określonej pozycji.|
|[equals](#equals)|Porównuje dwa pamięci podręczne dla równości.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<buforów >

**Namespace:** stdext

## <a name="allocate"></a>  sync_shared::allocate

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

Funkcja elementu członkowskiego blokuje mutex, wywołania `cache.allocate(count)`odblokowuje element mutex i zwraca wynik wcześniejszego wywołania `cache.allocate(count)`. `cache` reprezentuje bieżący obiekt z pamięci podręcznej.

## <a name="deallocate"></a>  sync_shared::deallocate

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

Ta funkcja elementu członkowskiego blokuje mutex, wywołania `cache.deallocate(ptr, count)`, gdzie `cache` reprezentuje obiektu pamięci podręcznej, a następnie odblokowuje element mutex.

## <a name="equals"></a>  sync_shared::Equals

Porównuje dwa pamięci podręczne dla równości.

```cpp
bool equals(const sync_shared<Cache>& Other) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Cache*|Typ pamięci podręcznej skojarzone z filtrem synchronizacji.|
|*Inne*|Pamięć podręczna do porównania dla równości.|

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli wynikiem `cache.equals(Other.cache)`, gdzie `cache` reprezentuje obiektu pamięci podręcznej, jest **true**; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz także

[\<allocators — >](../standard-library/allocators-header.md)<br/>
