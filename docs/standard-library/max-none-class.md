---
title: max_none — Klasa
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::max_none
- allocators/stdext::max_none::allocated
- allocators/stdext::max_none::deallocated
- allocators/stdext::max_none::full
- allocators/stdext::max_none::released
- allocators/stdext::max_none::saved
helpviewer_keywords:
- stdext::max_none
- stdext::max_none [C++], allocated
- stdext::max_none [C++], deallocated
- stdext::max_none [C++], full
- stdext::max_none [C++], released
- stdext::max_none [C++], saved
ms.assetid: 12ab5376-412e-479c-86dc-2c3d6a3559b6
ms.openlocfilehash: c49ceec72be62d8ff3125f04d97bbb6952501677
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370981"
---
# <a name="max_none-class"></a>max_none — Klasa

Opisuje [obiekt klasy max,](../standard-library/allocators-header.md) który ogranicza [obiekt freelist](../standard-library/freelist-class.md) do maksymalnej długości zero.

## <a name="syntax"></a>Składnia

```cpp
template <std::size_t Max>
class max_none
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Max*|Max klasa, która określa maksymalną liczbę elementów do przechowywania w `freelist`.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[Przydzielone](#allocated)|Zwiększa liczbę przydzielonych bloków pamięci.|
|[Dealokowane](#deallocated)|Zmniejsza liczbę przydzielonych bloków pamięci.|
|[Pełne](#full)|Zwraca wartość, która określa, czy więcej bloków pamięci powinny zostać dodane do listy wolnych.|
|[Wydany](#released)|Zmniejsza liczbę bloków pamięci na liście wolnych.|
|[Zapisano](#saved)|Zwiększa liczbę bloków pamięci na liście wolnych.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<alokatory>

**Obszar nazw:** stdext

## <a name="max_noneallocated"></a><a name="allocated"></a>max_none::przydzielone

Zwiększa liczbę przydzielonych bloków pamięci.

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*_Nx*|Wartość przyrostu.|

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego nic nie robi. Jest wywoływana po każdym `cache_freelist::allocate` pomyślnym wywołaniu przez operatora **nowego**. Argument *_Nx* jest liczba bloków pamięci w fragmencie przydzielonym przez operatora **new**.

## <a name="max_nonedeallocated"></a><a name="deallocated"></a>max_none::dlokowane

Zmniejsza liczbę przydzielonych bloków pamięci.

```cpp
void deallocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*_Nx*|Wartość przyrostu.|

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego nic nie robi. Ta funkcja elementu członkowskiego jest `cache_freelist::deallocate` wywoływana po każdym wywołaniu przez operatora **delete**. Argument *_Nx* jest liczba bloków pamięci w fragmencie cofnięte przez operatora **usunąć**.

## <a name="max_nonefull"></a><a name="full"></a>max_none::pełna

Zwraca wartość, która określa, czy więcej bloków pamięci powinny zostać dodane do listy wolnych.

```cpp
bool full();
```

### <a name="return-value"></a>Wartość zwracana

Ta funkcja elementu członkowskiego zawsze zwraca **wartość true**.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu `cache_freelist::deallocate`członkowskiego jest wywoływana przez . Jeśli wywołanie **true**zwraca `deallocate` true , umieszcza blok pamięci na liście wolnych; jeśli zwraca **false**false `deallocate` , wywołuje **delete** operatora, aby zdyskcesizować blok.

## <a name="max_nonereleased"></a><a name="released"></a>max_none::zwolniony

Zmniejsza liczbę bloków pamięci na liście wolnych.

```cpp
void released();
```

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego nic nie robi. Funkcja `released` elementu członkowskiego bieżącej klasy `cache_freelist::allocate` max jest wywoływana za każdym razem, gdy usuwa blok pamięci z listy wolnych.

## <a name="max_nonesaved"></a><a name="saved"></a>max_none::zapisane

Zwiększa liczbę bloków pamięci na liście wolnych.

```cpp
void saved();
```

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego nic nie robi. Jest wywoływana `cache_freelist::deallocate` przez każdym razem, gdy umieszcza blok pamięci na liście wolnych.

## <a name="see-also"></a>Zobacz też

[\<>alokatorów](../standard-library/allocators-header.md)
