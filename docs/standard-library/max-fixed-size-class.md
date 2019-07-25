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
ms.openlocfilehash: bbc39a169f9a4bbac3e78b208b3a1a31e4e30ff2
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456378"
---
# <a name="maxfixedsize-class"></a>max_fixed_size — Klasa

Opisuje obiekt [Max Class](../standard-library/allocators-header.md) , który ogranicza obiekt [freelist](../standard-library/freelist-class.md) do stałej maksymalnej długości.

## <a name="syntax"></a>Składnia

```cpp
template <std::size_t Max>
class max_fixed_size
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Maksymalna*|Maksymalna Klasa, która określa maksymalną liczbę elementów do przechowywania w `freelist`.|

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[max_fixed_size](#max_fixed_size)|Konstruuje obiekt typu `max_fixed_size`.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[rozdziela](#allocated)|Zwiększa liczbę przydzieloną bloków pamięci.|
|[bez alokacji](#deallocated)|Zmniejsza liczbę przydzieloną bloków pamięci.|
|[full](#full)|Zwraca wartość określającą, czy więcej bloków pamięci należy dodać do listy bezpłatnych.|
|[zwolni](#released)|Zmniejsza liczbę bloków pamięci na liście bezpłatnych.|
|[zapis](#saved)|Zwiększa liczbę bloków pamięci na liście bezpłatnych.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<przypisania >

**Przestrzeń nazw:** stdext

## <a name="allocated"></a>max_fixed_size:: przydzielono

Zwiększa liczbę przydzieloną bloków pamięci.

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*_Nx*|Wartość przyrostu.|

### <a name="remarks"></a>Uwagi

Funkcja członkowska nic nie robi. Ta funkcja członkowska jest wywoływana po każdym pomyślnym wywołaniu `cache_freelist::allocate` do operatora **New**. Argument *_Nx* jest liczbą bloków pamięci w fragmencie przydzielonym przez operator **New**.

## <a name="deallocated"></a>max_fixed_size::d eallocated

Zmniejsza liczbę przydzieloną bloków pamięci.

```cpp
void deallocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*_Nx*|Wartość przyrostu.|

### <a name="remarks"></a>Uwagi

Funkcja członkowska nic nie robi. Ta funkcja członkowska jest wywoływana po każdym wywołaniu `cache_freelist::deallocate` operatora, aby operator został **usunięty**. Argument *_Nx* to liczba bloków pamięci w cofnięciu przydziału fragmentów przez operator **delete**.

## <a name="full"></a>max_fixed_size:: Full

Zwraca wartość określającą, czy więcej bloków pamięci należy dodać do listy bezpłatnych.

```cpp
bool full();
```

### <a name="return-value"></a>Wartość zwracana

**prawda** , `Max <= _Nblocks`Jeśli; w przeciwnym razie, **Fałsz**.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest wywoływana `cache_freelist::deallocate`przez. Jeśli wywołanie zwraca **wartość true**, `deallocate` umieszcza blok pamięci na liście bezpłatnych. Jeśli zwróci wartość false, `deallocate` wywołania operatora **delete** w celu cofnięcia alokacji bloku.

## <a name="max_fixed_size"></a>max_fixed_size::max_fixed_size

Konstruuje obiekt typu `max_fixed_size`.

```cpp
max_fixed_size();
```

### <a name="remarks"></a>Uwagi

Ten konstruktor inicjuje wartość `_Nblocks` przechowywaną na zero.

## <a name="released"></a>max_fixed_size:: wydana

Zmniejsza liczbę bloków pamięci na liście bezpłatnych.

```cpp
void released();
```

### <a name="remarks"></a>Uwagi

Zmniejsza przechowywaną wartość `_Nblocks`. Funkcja członkowska bieżącej [klasy Max](../standard-library/allocators-header.md) jest wywoływana za `cache_freelist::allocate` każdym razem, gdy usuwa blok pamięci z listy bezpłatnych. `released`

## <a name="saved"></a>max_fixed_size:: Zapisano

Zwiększa liczbę bloków pamięci na liście bezpłatnych.

```cpp
void saved();
```

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska zwiększa przechowywaną wartość `_Nblocks`. Ta funkcja członkowska jest wywoływana `cache_freelist::deallocate` za każdym razem, gdy umieszcza blok pamięci na liście bezpłatnych.

## <a name="see-also"></a>Zobacz także

[\<allocators>](../standard-library/allocators-header.md)
