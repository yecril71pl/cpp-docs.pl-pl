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
ms.openlocfilehash: b296c641be68efac7410328a448a4ad2bd0fa88e
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626829"
---
# <a name="max_none-class"></a>max_none — Klasa

Opisuje obiekt [klasy maksymalnej](../standard-library/allocators-header.md) , który ogranicza obiekt [freelist](../standard-library/freelist-class.md) do maksymalnej długości równej zero.

## <a name="syntax"></a>Składnia

```cpp
template <std::size_t Max>
class max_none
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Maksymalny*|Maksymalna Klasa, która określa maksymalną liczbę elementów do zapisania w `freelist`.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[rozdziela](#allocated)|Zwiększa liczbę przydzieloną bloków pamięci.|
|[bez alokacji](#deallocated)|Zmniejsza liczbę przydzieloną bloków pamięci.|
|[szczegółowe](#full)|Zwraca wartość określającą, czy więcej bloków pamięci należy dodać do listy bezpłatnych.|
|[zwolni](#released)|Zmniejsza liczbę bloków pamięci na liście bezpłatnych.|
|[zapis](#saved)|Zwiększa liczbę bloków pamięci na liście bezpłatnych.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<allocators >

**Przestrzeń nazw:** stdext

## <a name="allocated"></a>max_none:: przydzielono

Zwiększa liczbę przydzieloną bloków pamięci.

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*_Nx*|Wartość przyrostu.|

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska nic nie robi. Jest wywoływana po każdym pomyślnym wywołaniu przez `cache_freelist::allocate` operatora **New**. Argument *_Nx* jest liczbą bloków pamięci w fragmencie przydzielonym przez operator **New**.

## <a name="deallocated"></a>max_none::d eallocated

Zmniejsza liczbę przydzieloną bloków pamięci.

```cpp
void deallocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*_Nx*|Wartość przyrostu.|

### <a name="remarks"></a>Uwagi

Funkcja członkowska nic nie robi. Ta funkcja członkowska jest wywoływana po każdym wywołaniu przez `cache_freelist::deallocate` operatora **delete**. Argument *_Nx* to liczba bloków pamięci w cofnięciu przydziału fragmentów przez operator **delete**.

## <a name="full"></a>max_none:: Full

Zwraca wartość określającą, czy więcej bloków pamięci należy dodać do listy bezpłatnych.

```cpp
bool full();
```

### <a name="return-value"></a>Wartość zwracana

Ta funkcja członkowska zawsze zwraca **wartość true**.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest wywoływana przez `cache_freelist::deallocate`. Jeśli wywołanie zwróci **wartość true**, `deallocate` umieszcza blok pamięci na liście bezpłatnych. Jeśli zwraca **wartość false**, `deallocate` wywołuje operatora **delete** w celu cofnięcia alokacji bloku.

## <a name="released"></a>max_none:: wydana

Zmniejsza liczbę bloków pamięci na liście bezpłatnych.

```cpp
void released();
```

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska nic nie robi. Funkcja członkowska `released` bieżącej klasy Max jest wywoływana przez `cache_freelist::allocate` za każdym razem, gdy usuwa blok pamięci z listy bezpłatnych.

## <a name="saved"></a>max_none:: Zapisano

Zwiększa liczbę bloków pamięci na liście bezpłatnych.

```cpp
void saved();
```

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska nic nie robi. Jest wywoływana przez `cache_freelist::deallocate` za każdym razem, gdy umieszcza blok pamięci na liście bezpłatnych.

## <a name="see-also"></a>Zobacz także

[\<allocators >](../standard-library/allocators-header.md)
