---
title: sync_none — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- allocators/stdext::sync_none
- allocators/stdext::sync_none::allocate
- allocators/stdext::sync_none::deallocate
- allocators/stdext::sync_none::equals
dev_langs:
- C++
helpviewer_keywords:
- stdext::sync_none
- stdext::sync_none [C++], allocate
- stdext::sync_none [C++], deallocate
- stdext::sync_none [C++], equals
ms.assetid: f7473cee-14f3-4fe1-88bc-68cd085e59e1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9fe7672a925105bff3b63032a709353388143c0c
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38953013"
---
# <a name="syncnone-class"></a>sync_none — Klasa

W tym artykule opisano [filtr synchronizacji](../standard-library/allocators-header.md) zapewniający Brak synchronizacji.

## <a name="syntax"></a>Składnia

```cpp
template <class Cache>
class sync_none
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`Cache`|Typ pamięci podręcznej skojarzone z filtrem synchronizacji. Może to być [cache_chunklist](../standard-library/cache-chunklist-class.md), [cache_freelist](../standard-library/cache-freelist-class.md), lub [cache_suballoc](../standard-library/cache-suballoc-class.md).|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[allocate](#allocate)|Przydziela blok pamięci.|
|[Cofnij Przydział](#deallocate)|Zwalnia określoną liczbę obiektów z pamięci masowej rozpoczynający się od określonej pozycji.|
|[equals](#equals)|Porównuje dwa pamięci podręczne dla równości.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<buforów >

**Namespace:** stdext

## <a name="allocate"></a>  sync_none::allocate

Przydziela blok pamięci.

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Liczba*|Liczba elementów w tablicy do przydzielenia.|

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca `cache.allocate(count)`, gdzie `cache` jest buforowany obiekt.

## <a name="deallocate"></a>  sync_none::deallocate

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

Wywołania funkcji elementu członkowskiego `cache.deallocate(ptr, count)`, gdzie `cache` reprezentuje buforowany obiekt.

## <a name="equals"></a>  sync_none::Equals

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

Funkcja elementu członkowskiego zwraca zawsze **true**.

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz także

[\<allocators — >](../standard-library/allocators-header.md)<br/>
