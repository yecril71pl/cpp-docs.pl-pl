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
ms.openlocfilehash: e0254563cc60db4a171527735b373c2954a5a9e5
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/18/2020
ms.locfileid: "88561963"
---
# <a name="max_unbounded-class"></a>max_unbounded — Klasa

Opisuje obiekt [Max Class](../standard-library/allocators-header.md) , który nie ogranicza maksymalnej długości obiektu [freelist](../standard-library/freelist-class.md) .

## <a name="syntax"></a>Składnia

```cpp
class max_unbounded
```

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[rozdziela](#allocated)|Zwiększa liczbę przydzieloną bloków pamięci.|
|[bez alokacji](#deallocated)|Zmniejsza liczbę przydzieloną bloków pamięci.|
|[szczegółowe](#full)|Zwraca wartość określającą, czy więcej bloków pamięci należy dodać do listy bezpłatnych.|
|[zwolni](#released)|Zmniejsza liczbę bloków pamięci na liście bezpłatnych.|
|[zapis](#saved)|Zwiększa liczbę bloków pamięci na liście bezpłatnych.|

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<allocators>

**Przestrzeń nazw:** stdext

## <a name="max_unboundedallocated"></a><a name="allocated"></a> max_unbounded:: przydzielono

Zwiększa liczbę przydzieloną bloków pamięci.

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parametry

*_Nx*\
Wartość przyrostu.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska nic nie robi. Jest wywoływana po każdym pomyślnym wywołaniu `cache_freelist::allocate` operatora by **`new`** . Argument *_Nx* jest liczbą bloków pamięci w fragmencie przydzielonym przez operatora **`new`** .

## <a name="max_unboundeddeallocated"></a><a name="deallocated"></a> max_unbounded::d eallocated

Zmniejsza liczbę przydzieloną bloków pamięci.

```cpp
void deallocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parametry

*_Nx*\
Wartość przyrostu.

### <a name="remarks"></a>Uwagi

Funkcja członkowska nic nie robi. Ta funkcja członkowska jest wywoływana po każdym wywołaniu `cache_freelist::deallocate` operatora **`delete`** . Argument *_Nx* jest liczbą bloków pamięci w przydzielonym operatorze fragmentów **`delete`** .

## <a name="max_unboundedfull"></a><a name="full"></a> max_unbounded:: Full

Zwraca wartość określającą, czy więcej bloków pamięci należy dodać do listy bezpłatnych.

```cpp
bool full();
```

### <a name="return-value"></a>Wartość zwracana

Funkcja członkowska zawsze zwraca wartość **`false`** .

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest wywoływana przez `cache_freelist::deallocate` . Jeśli wywołanie zwraca **`true`** , `deallocate` umieszcza blok pamięci na liście bezpłatnej; jeśli zwraca wartość false, `deallocate` operator wywołań, **`delete`** Aby cofnąć alokację bloku.

## <a name="max_unboundedreleased"></a><a name="released"></a> max_unbounded:: wydano

Zmniejsza liczbę bloków pamięci na liście bezpłatnych.

```cpp
void released();
```

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska nic nie robi. `released`Funkcja członkowska bieżącej klasy Max jest wywoływana za `cache_freelist::allocate` każdym razem, gdy usuwa blok pamięci z listy bezpłatnych.

## <a name="max_unboundedsaved"></a><a name="saved"></a> max_unbounded:: Zapisano

Zwiększa liczbę bloków pamięci na liście bezpłatnych.

```cpp
void saved();
```

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska nic nie robi. Jest wywoływana za `cache_freelist::deallocate` każdym razem, gdy umieszcza blok pamięci na liście bezpłatnych.

## <a name="see-also"></a>Zobacz też

[\<allocators>](../standard-library/allocators-header.md)
