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
ms.openlocfilehash: 41ada338d9b8546202ecd49ff975f9642f190ba0
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/18/2020
ms.locfileid: "88560546"
---
# <a name="max_none-class"></a>max_none — Klasa

Opisuje obiekt [klasy maksymalnej](../standard-library/allocators-header.md) , który ogranicza obiekt [freelist](../standard-library/freelist-class.md) do maksymalnej długości równej zero.

## <a name="syntax"></a>Składnia

```cpp
template <std::size_t Max>
class max_none
```

### <a name="parameters"></a>Parametry

*Maksymalny*\
Maksymalna Klasa, która określa maksymalną liczbę elementów do przechowywania w `freelist` .

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

## <a name="max_noneallocated"></a><a name="allocated"></a> max_none:: przydzielono

Zwiększa liczbę przydzieloną bloków pamięci.

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parametry

*_Nx*\
Wartość przyrostu.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska nic nie robi. Jest wywoływana po każdym pomyślnym wywołaniu `cache_freelist::allocate` operatora by **`new`** . Argument *_Nx* jest liczbą bloków pamięci w fragmencie przydzielonym przez operatora **`new`** .

## <a name="max_nonedeallocated"></a><a name="deallocated"></a> max_none::d eallocated

Zmniejsza liczbę przydzieloną bloków pamięci.

```cpp
void deallocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parametry

*_Nx*\
Wartość przyrostu.

### <a name="remarks"></a>Uwagi

Funkcja członkowska nic nie robi. Ta funkcja członkowska jest wywoływana po każdym wywołaniu `cache_freelist::deallocate` operatora **`delete`** . Argument *_Nx* jest liczbą bloków pamięci w przydzielonym operatorze fragmentów **`delete`** .

## <a name="max_nonefull"></a><a name="full"></a> max_none:: Full

Zwraca wartość określającą, czy więcej bloków pamięci należy dodać do listy bezpłatnych.

```cpp
bool full();
```

### <a name="return-value"></a>Wartość zwracana

Ta funkcja członkowska zawsze zwraca wartość **`true`** .

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest wywoływana przez `cache_freelist::deallocate` . Jeśli wywołanie zwraca **`true`** , `deallocate` umieszcza blok pamięci na liście bezpłatnej. Jeśli zwróci **`false`** , `deallocate` operator wywołań, **`delete`** Aby cofnąć alokację bloku.

## <a name="max_nonereleased"></a><a name="released"></a> max_none:: wydano

Zmniejsza liczbę bloków pamięci na liście bezpłatnych.

```cpp
void released();
```

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska nic nie robi. `released`Funkcja członkowska bieżącej klasy Max jest wywoływana za `cache_freelist::allocate` każdym razem, gdy usuwa blok pamięci z listy bezpłatnych.

## <a name="max_nonesaved"></a><a name="saved"></a> max_none:: Zapisano

Zwiększa liczbę bloków pamięci na liście bezpłatnych.

```cpp
void saved();
```

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska nic nie robi. Jest wywoływana za `cache_freelist::deallocate` każdym razem, gdy umieszcza blok pamięci na liście bezpłatnych.

## <a name="see-also"></a>Zobacz też

[\<allocators>](../standard-library/allocators-header.md)
