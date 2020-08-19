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
ms.openlocfilehash: 53d2603c82e94710ed687dce4caeec24aeb2f60a
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/18/2020
ms.locfileid: "88561651"
---
# <a name="max_variable_size-class"></a>max_variable_size — Klasa

Opisuje obiekt [klasy maksymalnej](../standard-library/allocators-header.md) , który ogranicza obiekt [freelist](../standard-library/freelist-class.md) do maksymalnej długości, która jest w przybliżeniu proporcjonalna do liczby przydzielone bloków pamięci.

## <a name="syntax"></a>Składnia

```cpp
class max_variable_size
```

### <a name="constructors"></a>Konstruktory

|Konstruktor|Opis|
|-|-|
|[max_variable_size](#max_variable_size)|Konstruuje obiekt typu `max_variable_size` .|

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

## <a name="max_variable_sizeallocated"></a><a name="allocated"></a> max_variable_size:: przydzielono

Zwiększa liczbę przydzieloną bloków pamięci.

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parametry

*_Nx*\
Wartość przyrostu.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska dodaje *_Nx* do przechowywanej wartości `_Nallocs` . Ta funkcja członkowska jest wywoływana po każdym pomyślnym wywołaniu `cache_freelist::allocate` operatora **`new`** . Argument *_Nx* jest liczbą bloków pamięci w fragmencie przydzielonym przez operatora **`new`** .

## <a name="max_variable_sizedeallocated"></a><a name="deallocated"></a> max_variable_size::d eallocated

Zmniejsza liczbę przydzieloną bloków pamięci.

```cpp
void deallocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parametry

*_Nx*\
Wartość przyrostu.

### <a name="remarks"></a>Uwagi

Funkcja członkowska odejmuje *_Nx* od przechowywanej wartości `_Nallocs` . Ta funkcja członkowska jest wywoływana po każdym wywołaniu `cache_freelist::deallocate` operatora **`delete`** . Argument *_Nx* jest liczbą bloków pamięci w przydzielonym operatorze fragmentów **`delete`** .

## <a name="max_variable_sizefull"></a><a name="full"></a> max_variable_size:: Full

Zwraca wartość określającą, czy więcej bloków pamięci należy dodać do listy bezpłatnych.

```cpp
bool full();
```

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli `_Nallocs / 16 + 16 <= _Nblocks` .

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest wywoływana przez `cache_freelist::deallocate` . Jeśli wywołanie zwraca **`true`** , `deallocate` umieszcza blok pamięci na liście bezpłatnej; jeśli zwraca wartość false, `deallocate` operator wywołań, **`delete`** Aby cofnąć alokację bloku.

## <a name="max_variable_sizemax_variable_size"></a><a name="max_variable_size"></a> max_variable_size:: max_variable_size

Konstruuje obiekt typu `max_variable_size` .

```cpp
max_variable_size();
```

### <a name="remarks"></a>Uwagi

Konstruktor inicjuje przechowywane wartości `_Nblocks` i `_Nallocs` zero.

## <a name="max_variable_sizereleased"></a><a name="released"></a> max_variable_size:: wydano

Zmniejsza liczbę bloków pamięci na liście bezpłatnych.

```cpp
void released();
```

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska zmniejsza przechowywaną wartość `_Nblocks` . `released`Funkcja członkowska bieżącej klasy Max jest wywoływana za `cache_freelist::allocate` każdym razem, gdy usuwa blok pamięci z listy bezpłatnych.

## <a name="max_variable_sizesaved"></a><a name="saved"></a> max_variable_size:: Zapisano

Zwiększa liczbę bloków pamięci na liście bezpłatnych.

```cpp
void saved();
```

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska zwiększa przechowywaną wartość `_Nblocks` . Ta funkcja członkowska jest wywoływana za `cache_freelist::deallocate` każdym razem, gdy umieszcza blok pamięci na liście bezpłatnych.

## <a name="see-also"></a>Zobacz też

[\<allocators>](../standard-library/allocators-header.md)
