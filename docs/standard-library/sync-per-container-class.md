---
title: sync_per_container — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- allocators/stdext::sync_per_container
- allocators/stdext::sync_per_container::equals
dev_langs:
- C++
helpviewer_keywords:
- sync_per_container class
ms.assetid: 0b4b2904-b668-4d94-a422-d4f919cbffab
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: af1db124d7fa73a9483d2c77f0a1e78349224023
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="syncpercontainer-class"></a>sync_per_container — Klasa

W tym artykule opisano [filtr synchronizacji](../standard-library/allocators-header.md) zapewnia obiektu osobne dla każdego obiektu przydzielania.

## <a name="syntax"></a>Składnia

```cpp
template <class Cache>
class sync_per_container
 : public Cache
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`Cache`|Typ pamięci podręcznej skojarzone z filtrem synchronizacji. Może to być [cache_chunklist —](../standard-library/cache-chunklist-class.md), [cache_freelist —](../standard-library/cache-freelist-class.md), lub [cache_suballoc —](../standard-library/cache-suballoc-class.md).|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[equals](#equals)|Porównuje dwa pamięci podręcznych pod kątem równości.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<allocators — >

**Namespace:** stdext —

## <a name="equals"></a>  sync_per_container::Equals

Porównuje dwa pamięci podręcznych pod kątem równości.

```cpp
bool equals(const sync_per_container<Cache>& Other) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`Cache`|Buforowany obiekt filtr synchronizacji.|
|`Other`|Buforowany obiekt do porównania równości.|

### <a name="return-value"></a>Wartość zwracana

Funkcja członkowska zawsze zwraca `false`.

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz także

[\<allocators — >](../standard-library/allocators-header.md)<br/>
