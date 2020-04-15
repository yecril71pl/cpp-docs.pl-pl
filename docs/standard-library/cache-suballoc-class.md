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
ms.openlocfilehash: 55860a65fc77f834ed699f3a5114768b7efdde6f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366730"
---
# <a name="cache_suballoc-class"></a>cache_suballoc — Klasa

Definiuje [alokator bloków,](../standard-library/allocators-header.md) który przydziela i przydziela bloki pamięci o jednym rozmiarze.

## <a name="syntax"></a>Składnia

```cpp
template <std::size_t Sz, size_t Nelts = 20>
class cache_suballoc
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Sz*|Liczba elementów w tablicy, które mają zostać przydzielone.|

## <a name="remarks"></a>Uwagi

Szablon klasy cache_suballoc przechowuje przydzielone bloki pamięci z przydziałem na liście `freelist<sizeof(Type), max_unbounded>`wolnych o nieograniczonej długości, używając i suballocates bloków pamięci z większego fragmentu przydzielonego **operatorowi nowy,** gdy lista wolna jest pusta.

Każdy fragment `Sz * Nelts` zawiera bajty pamięci użytkowej i danych, które **operator nowy** i **operator usunąć** wymagają. Przydzielone fragmenty nigdy nie są zwalniane.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[cache_suballoc](#cache_suballoc)|Konstruuje obiekt `cache_suballoc`typu .|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[allocate](#allocate)|Przydziela blok pamięci.|
|[Deallocate](#deallocate)|Zwalnia określoną liczbę obiektów z magazynu, począwszy od określonej pozycji.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<alokatory>

**Obszar nazw:** stdext

## <a name="cache_suballocallocate"></a><a name="allocate"></a>cache_suballoc::przydziel

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

## <a name="cache_suballoccache_suballoc"></a><a name="cache_suballoc"></a>cache_suballoc::cache_suballoc

Konstruuje obiekt `cache_suballoc`typu .

```cpp
cache_suballoc();
```

### <a name="remarks"></a>Uwagi

## <a name="cache_suballocdeallocate"></a><a name="deallocate"></a>cache_suballoc::dlokalizuj

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

## <a name="see-also"></a>Zobacz też

[\<>alokatorów](../standard-library/allocators-header.md)
