---
title: cache_freelist — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- allocators/stdext::cache_freelist
- allocators/stdext::cache_freelist::allocate
- allocators/stdext::cache_freelist::deallocate
dev_langs:
- C++
helpviewer_keywords:
- stdext::cache_freelist
- stdext::cache_freelist [C++], allocate
- stdext::cache_freelist [C++], deallocate
ms.assetid: 840694de-36ba-470f-8dae-2b723d5a8cd9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c3d3902d900e0dad5ec3e335e9c3424d58ee2674
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38960420"
---
# <a name="cachefreelist-class"></a>cache_freelist — Klasa

Definiuje [block alokatora](../standard-library/allocators-header.md) który przydziela i zwalnia bloki pamięci o rozmiarze jednego.

## <a name="syntax"></a>Składnia

```cpp
template <std::size_t Sz, class Max>
class cache_freelist
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Sz*|Liczba elementów w tablicy do przydzielenia.|
|*Maksymalna*|Klasa max reprezentujący maksymalny rozmiar wolnego listy. Może to być [max_fixed_size —](../standard-library/max-fixed-size-class.md), [max_none —](../standard-library/max-none-class.md), [max_unbounded —](../standard-library/max-unbounded-class.md), lub [max_variable_size —](../standard-library/max-variable-size-class.md).|

## <a name="remarks"></a>Uwagi

Cache_freelist — klasa szablonu przechowuje listę wolne bloki pamięci o rozmiarze *Sz*. Po zapełnieniu listy bezpłatne używa **operatora delete** można cofnąć alokacji pamięci blokuje. Bezpłatne lista jest pusta korzysta **nowy operator** przydzielić nowe bloki pamięci. Maksymalny rozmiar wolnego list jest określany przez klasę klasy max przekazanej *Max* parametru.

Każdy blok pamięci przechowuje *Sz* w bajtach dostępnej pamięci i danych, **nowy operator** i **operatora delete** wymagają.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[cache_freelist](#cache_freelist)|Tworzy obiekt typu `cache_freelist`.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[allocate](#allocate)|Przydziela blok pamięci.|
|[Cofnij Przydział](#deallocate)|Zwalnia określoną liczbę obiektów z pamięci masowej rozpoczynający się od określonej pozycji.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<buforów >

**Namespace:** stdext

## <a name="allocate"></a>  cache_freelist::allocate

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

## <a name="cache_freelist"></a>  cache_freelist::cache_freelist

Tworzy obiekt typu `cache_freelist`.

```cpp
cache_freelist();
```

### <a name="remarks"></a>Uwagi

## <a name="deallocate"></a>  cache_freelist::deallocate

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

## <a name="see-also"></a>Zobacz także

[\<allocators — >](../standard-library/allocators-header.md)<br/>
