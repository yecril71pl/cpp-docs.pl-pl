---
title: max_unbounded — Klasa
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::max_unbounded
- allocators/stdext::max_unbounded::allocated
- allocators/stdext::max_unbounded::deallocated
- allocators/stdext::max_unbounded::full
- allocators/stdext::max_unbounded::released
- allocators/stdext::max_unbounded::saved
helpviewer_keywords:
- stdext::max_unbounded
- stdext::max_unbounded [C++], allocated
- stdext::max_unbounded [C++], deallocated
- stdext::max_unbounded [C++], full
- stdext::max_unbounded [C++], released
- stdext::max_unbounded [C++], saved
ms.assetid: e34627a9-c231-4031-a483-cbb0514fff46
ms.openlocfilehash: fbc4351297ab8a3cc90a2a77fa31c3b134f10eab
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370991"
---
# <a name="max_unbounded-class"></a>max_unbounded — Klasa

Opisuje [obiekt klasy max,](../standard-library/allocators-header.md) który nie ogranicza maksymalnej długości obiektu [freelist.](../standard-library/freelist-class.md)

## <a name="syntax"></a>Składnia

```cpp
class max_unbounded
```

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

## <a name="max_unboundedallocated"></a><a name="allocated"></a>max_unbounded::przydzielone

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

## <a name="max_unboundeddeallocated"></a><a name="deallocated"></a>max_unbounded::dlokowane

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

## <a name="max_unboundedfull"></a><a name="full"></a>max_unbounded::pełna

Zwraca wartość, która określa, czy więcej bloków pamięci powinny zostać dodane do listy wolnych.

```cpp
bool full();
```

### <a name="return-value"></a>Wartość zwracana

Funkcja elementu członkowskiego zawsze zwraca **wartość false**.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu `cache_freelist::deallocate`członkowskiego jest wywoływana przez . Jeśli wywołanie **true**zwraca `deallocate` true , umieszcza blok pamięci na liście wolnych; jeśli zwraca false, `deallocate` wywołuje delete operatora, aby zdyskontować blok. **delete**

## <a name="max_unboundedreleased"></a><a name="released"></a>max_unbounded::zwolniony

Zmniejsza liczbę bloków pamięci na liście wolnych.

```cpp
void released();
```

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego nic nie robi. Funkcja `released` elementu członkowskiego bieżącej klasy `cache_freelist::allocate` max jest wywoływana za każdym razem, gdy usuwa blok pamięci z listy wolnych.

## <a name="max_unboundedsaved"></a><a name="saved"></a>max_unbounded::zapisane

Zwiększa liczbę bloków pamięci na liście wolnych.

```cpp
void saved();
```

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego nic nie robi. Jest wywoływana `cache_freelist::deallocate` przez każdym razem, gdy umieszcza blok pamięci na liście wolnych.

## <a name="see-also"></a>Zobacz też

[\<>alokatorów](../standard-library/allocators-header.md)
