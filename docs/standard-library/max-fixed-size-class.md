---
title: max_fixed_size — Klasa
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::max_fixed_size
- allocators/stdext::max_fixed_size::allocated
- allocators/stdext::max_fixed_size::deallocated
- allocators/stdext::max_fixed_size::full
- allocators/stdext::max_fixed_size::released
- allocators/stdext::max_fixed_size::saved
helpviewer_keywords:
- stdext::max_fixed_size
- stdext::max_fixed_size [C++], allocated
- stdext::max_fixed_size [C++], deallocated
- stdext::max_fixed_size [C++], full
- stdext::max_fixed_size [C++], released
- stdext::max_fixed_size [C++], saved
ms.assetid: 8c8f4588-37e9-4579-8168-ba3553800914
ms.openlocfilehash: 23aa10a3398c3f20de73eb2ac6fa1372efdc32e5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228209"
---
# <a name="max_fixed_size-class"></a>max_fixed_size — Klasa

Opisuje obiekt [Max Class](../standard-library/allocators-header.md) , który ogranicza obiekt [freelist](../standard-library/freelist-class.md) do stałej maksymalnej długości.

## <a name="syntax"></a>Składnia

```cpp
template <std::size_t Max>
class max_fixed_size
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Maksymalny*|Maksymalna Klasa, która określa maksymalną liczbę elementów do przechowywania w `freelist` .|

### <a name="constructors"></a>Konstruktory

|Konstruktor|Opis|
|-|-|
|[max_fixed_size](#max_fixed_size)|Konstruuje obiekt typu `max_fixed_size` .|

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

## <a name="max_fixed_sizeallocated"></a><a name="allocated"></a>max_fixed_size:: przydzielono

Zwiększa liczbę przydzieloną bloków pamięci.

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*_Nx*|Wartość przyrostu.|

### <a name="remarks"></a>Uwagi

Funkcja członkowska nic nie robi. Ta funkcja członkowska jest wywoływana po każdym pomyślnym wywołaniu `cache_freelist::allocate` operatora **`new`** . Argument *_Nx* jest liczbą bloków pamięci w fragmencie przydzielonym przez operatora **`new`** .

## <a name="max_fixed_sizedeallocated"></a><a name="deallocated"></a>max_fixed_size::d eallocated

Zmniejsza liczbę przydzieloną bloków pamięci.

```cpp
void deallocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*_Nx*|Wartość przyrostu.|

### <a name="remarks"></a>Uwagi

Funkcja członkowska nic nie robi. Ta funkcja członkowska jest wywoływana po każdym wywołaniu `cache_freelist::deallocate` operatora **`delete`** . Argument *_Nx* jest liczbą bloków pamięci w przydzielonym operatorze fragmentów **`delete`** .

## <a name="max_fixed_sizefull"></a><a name="full"></a>max_fixed_size:: Full

Zwraca wartość określającą, czy więcej bloków pamięci należy dodać do listy bezpłatnych.

```cpp
bool full();
```

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli `Max <= _Nblocks` ; w przeciwnym razie, **`false`** .

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest wywoływana przez `cache_freelist::deallocate` . Jeśli wywołanie zwraca **`true`** , `deallocate` umieszcza blok pamięci na liście bezpłatnej; jeśli zwraca wartość false, `deallocate` operator wywołań, **`delete`** Aby cofnąć alokację bloku.

## <a name="max_fixed_sizemax_fixed_size"></a><a name="max_fixed_size"></a>max_fixed_size:: max_fixed_size

Konstruuje obiekt typu `max_fixed_size` .

```cpp
max_fixed_size();
```

### <a name="remarks"></a>Uwagi

Ten konstruktor inicjuje wartość przechowywaną `_Nblocks` na zero.

## <a name="max_fixed_sizereleased"></a><a name="released"></a>max_fixed_size:: wydano

Zmniejsza liczbę bloków pamięci na liście bezpłatnych.

```cpp
void released();
```

### <a name="remarks"></a>Uwagi

Zmniejsza przechowywaną wartość `_Nblocks` . `released`Funkcja członkowska bieżącej [klasy Max](../standard-library/allocators-header.md) jest wywoływana za `cache_freelist::allocate` każdym razem, gdy usuwa blok pamięci z listy bezpłatnych.

## <a name="max_fixed_sizesaved"></a><a name="saved"></a>max_fixed_size:: Zapisano

Zwiększa liczbę bloków pamięci na liście bezpłatnych.

```cpp
void saved();
```

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska zwiększa przechowywaną wartość `_Nblocks` . Ta funkcja członkowska jest wywoływana za `cache_freelist::deallocate` każdym razem, gdy umieszcza blok pamięci na liście bezpłatnych.

## <a name="see-also"></a>Zobacz także

[\<allocators>](../standard-library/allocators-header.md)
