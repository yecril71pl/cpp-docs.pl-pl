---
title: max_variable_size — Klasa
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::max_variable_size
- allocators/stdext::max_variable_size::allocated
- allocators/stdext::max_variable_size::deallocated
- allocators/stdext::max_variable_size::full
- allocators/stdext::max_variable_size::released
- allocators/stdext::max_variable_size::saved
helpviewer_keywords:
- stdext::max_variable_size
- stdext::max_variable_size [C++], allocated
- stdext::max_variable_size [C++], deallocated
- stdext::max_variable_size [C++], full
- stdext::max_variable_size [C++], released
- stdext::max_variable_size [C++], saved
ms.assetid: 9f2e9df0-4148-4b37-bc30-f8eca0ef86ae
ms.openlocfilehash: f8b3c61676f784bf9369c22b5db97d7b251f7ac6
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447281"
---
# <a name="maxvariablesize-class"></a>max_variable_size — Klasa

Opisuje obiekt [klasy maksymalnej](../standard-library/allocators-header.md) , który ogranicza obiekt [freelist](../standard-library/freelist-class.md) do maksymalnej długości, która jest w przybliżeniu proporcjonalna do liczby przydzielone bloków pamięci.

## <a name="syntax"></a>Składnia

```cpp
class max_variable_size
```

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[max_variable_size](#max_variable_size)|Konstruuje obiekt typu `max_variable_size`.|

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

## <a name="allocated"></a>max_variable_size:: przydzielono

Zwiększa liczbę przydzieloną bloków pamięci.

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*_Nx*|Wartość przyrostu.|

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska dodaje *_Nx* do przechowywanej `_Nallocs`wartości. Ta funkcja członkowska jest wywoływana po każdym pomyślnym wywołaniu `cache_freelist::allocate` do operatora **New**. Argument *_Nx* jest liczbą bloków pamięci w fragmencie przydzielonym przez operator **New**.

## <a name="deallocated"></a>max_variable_size::d eallocated

Zmniejsza liczbę przydzieloną bloków pamięci.

```cpp
void deallocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*_Nx*|Wartość przyrostu.|

### <a name="remarks"></a>Uwagi

Funkcja członkowska odejmuje *_Nx* z wartości `_Nallocs`przechowywanej. Ta funkcja członkowska jest wywoływana po każdym wywołaniu `cache_freelist::deallocate` operatora, aby operator został **usunięty**. Argument *_Nx* to liczba bloków pamięci w cofnięciu przydziału fragmentów przez operator **delete**.

## <a name="full"></a>max_variable_size:: Full

Zwraca wartość określającą, czy więcej bloków pamięci należy dodać do listy bezpłatnych.

```cpp
bool full();
```

### <a name="return-value"></a>Wartość zwracana

**wartość true** , jeśli `_Nallocs / 16 + 16 <= _Nblocks`.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest wywoływana `cache_freelist::deallocate`przez. Jeśli wywołanie zwraca **wartość true**, `deallocate` umieszcza blok pamięci na liście bezpłatnych. Jeśli zwróci wartość false, `deallocate` wywołania operatora **delete** w celu cofnięcia alokacji bloku.

## <a name="max_variable_size"></a>max_variable_size::max_variable_size

Konstruuje obiekt typu `max_variable_size`.

```cpp
max_variable_size();
```

### <a name="remarks"></a>Uwagi

Konstruktor inicjuje przechowywane wartości `_Nblocks` i `_Nallocs` zero.

## <a name="released"></a>max_variable_size:: wydana

Zmniejsza liczbę bloków pamięci na liście bezpłatnych.

```cpp
void released();
```

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska zmniejsza przechowywaną wartość `_Nblocks`. Funkcja członkowska bieżącej klasy Max jest wywoływana za `cache_freelist::allocate` każdym razem, gdy usuwa blok pamięci z listy bezpłatnych. `released`

## <a name="saved"></a>max_variable_size:: Zapisano

Zwiększa liczbę bloków pamięci na liście bezpłatnych.

```cpp
void saved();
```

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska zwiększa przechowywaną wartość `_Nblocks`. Ta funkcja członkowska jest wywoływana `cache_freelist::deallocate` za każdym razem, gdy umieszcza blok pamięci na liście bezpłatnych.

## <a name="see-also"></a>Zobacz także

[\<allocators>](../standard-library/allocators-header.md)
