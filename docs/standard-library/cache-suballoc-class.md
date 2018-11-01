---
title: cache_suballoc — Klasa
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::cache_suballoc
- allocators/stdext::cache_suballoc::allocate
- allocators/stdext::cache_suballoc::deallocate
helpviewer_keywords:
- stdext::cache_suballoc
- stdext::cache_suballoc [C++], allocate
- stdext::cache_suballoc [C++], deallocate
ms.assetid: 9ea9c5e9-1dcc-45d0-b3a7-a56a93d88898
ms.openlocfilehash: 06d0ef390e6ae1980b9ab20b8ceb67213837148b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50438873"
---
# <a name="cachesuballoc-class"></a>cache_suballoc — Klasa

Definiuje [block alokatora](../standard-library/allocators-header.md) który przydziela i zwalnia bloki pamięci o rozmiarze jednego.

## <a name="syntax"></a>Składnia

```cpp
template <std::size_t Sz, size_t Nelts = 20>
class cache_suballoc
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Sz*|Liczba elementów w tablicy do przydzielenia.|

## <a name="remarks"></a>Uwagi

Cache_suballoc — klasa szablonu przechowuje bloki cofnięcia przydziału pamięci w bezpłatnej listę o długości niepowiązane przy użyciu `freelist<sizeof(Type), max_unbounded>`i suballocates bloki pamięci z większych fragment przydzielonymi **nowy operator** po liście bezpłatne pusty.

Każdy fragment zawiera `Sz * Nelts` w bajtach dostępnej pamięci i danych, **nowy operator** i **operatora delete** wymagają. Przydzielone fragmenty nigdy nie są zwalniane.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[cache_suballoc](#cache_suballoc)|Tworzy obiekt typu `cache_suballoc`.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[allocate](#allocate)|Przydziela blok pamięci.|
|[Cofnij Przydział](#deallocate)|Zwalnia określoną liczbę obiektów z pamięci masowej rozpoczynający się od określonej pozycji.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<buforów >

**Namespace:** stdext

## <a name="allocate"></a>  cache_suballoc::allocate

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

## <a name="cache_suballoc"></a>  cache_suballoc::cache_suballoc

Tworzy obiekt typu `cache_suballoc`.

```cpp
cache_suballoc();
```

### <a name="remarks"></a>Uwagi

## <a name="deallocate"></a>  cache_suballoc::deallocate

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
