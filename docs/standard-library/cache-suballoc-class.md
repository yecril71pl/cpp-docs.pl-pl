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
ms.openlocfilehash: 410cdc7bd45c54c252ce33c7d8e3e2f883ac0eb4
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/18/2020
ms.locfileid: "88560624"
---
# <a name="cache_suballoc-class"></a>cache_suballoc — Klasa

Definiuje [Alokator bloku](../standard-library/allocators-header.md) , który przydziela i cofa alokacje bloków pamięci o pojedynczym rozmiarze.

## <a name="syntax"></a>Składnia

```cpp
template <std::size_t Sz, size_t Nelts = 20>
class cache_suballoc
```

### <a name="parameters"></a>Parametry

*Sz*\
Liczba elementów w tablicy, która ma zostać przypisana.

## <a name="remarks"></a>Uwagi

Szablon klasy cache_suballoc przechowuje cofnięte alokacje bloków pamięci na wolnej liście o nieograniczonej długości, przy użyciu `freelist<sizeof(Type), max_unbounded>` i podporządkowania bloków pamięci z większego fragmentu przydzielonego za pomocą **operatora new** , gdy lista bezpłatna jest pusta.

Każdy fragment zawiera `Sz * Nelts` bajty użytecznej pamięci oraz dane, które **operator new** i **operator delete** wymagają. Przydzieloną fragmenty nie są nigdy zwalniane.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Opis|
|-|-|
|[cache_suballoc](#cache_suballoc)|Konstruuje obiekt typu `cache_suballoc` .|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[allocate](#allocate)|Przydziela blok pamięci.|
|[alokowany](#deallocate)|Zwalnia określoną liczbę obiektów z magazynu, zaczynając od określonej pozycji.|

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<allocators>

**Przestrzeń nazw:** stdext

## <a name="cache_suballocallocate"></a><a name="allocate"></a> cache_suballoc:: Allocate

Przydziela blok pamięci.

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>Parametry

*liczbą*\
Liczba elementów w tablicy, która ma zostać przypisana.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do przydzielony obiekt.

### <a name="remarks"></a>Uwagi

## <a name="cache_suballoccache_suballoc"></a><a name="cache_suballoc"></a> cache_suballoc:: cache_suballoc

Konstruuje obiekt typu `cache_suballoc` .

```cpp
cache_suballoc();
```

### <a name="remarks"></a>Uwagi

## <a name="cache_suballocdeallocate"></a><a name="deallocate"></a> cache_suballoc::d eallocate

Zwalnia określoną liczbę obiektów z magazynu, zaczynając od określonej pozycji.

```cpp
void deallocate(void* ptr, std::size_t count);
```

### <a name="parameters"></a>Parametry

*PTR*\
Wskaźnik do pierwszego obiektu do cofnięcia przydziału z magazynu.

*liczbą*\
Liczba obiektów do cofnięcia przydziału z magazynu.

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[\<allocators>](../standard-library/allocators-header.md)
