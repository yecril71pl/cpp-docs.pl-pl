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
ms.openlocfilehash: 08510ecc3b7469e8f88a61dcb0df28541e170892
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412959"
---
# <a name="maxfixedsize-class"></a>max_fixed_size — Klasa

W tym artykule opisano [maksymalnej liczby klas](../standard-library/allocators-header.md) obiekt, który ogranicza [FreeList —](../standard-library/freelist-class.md) obiekt do stałej długości maksymalnej.

## <a name="syntax"></a>Składnia

```cpp
template <std::size_t Max>
class max_fixed_size
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Maksymalna*|Maksymalna klasę, która określa maksymalną liczbę elementów do przechowywania w `freelist`.|

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[max_fixed_size](#max_fixed_size)|Tworzy obiekt typu `max_fixed_size`.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[przydzielona](#allocated)|Zwiększa liczbę bloków ilość przydzielonej pamięci.|
|[Cofnięto alokację](#deallocated)|Dekrementuje liczbę przydzielonych bloków pamięci.|
|[full](#full)|Zwraca wartość określającą, czy więcej bloków pamięci powinna być dodana do listy bezpłatne.|
|[Wydana](#released)|Zmniejsza liczbę pamięci blokuje się na liście bezpłatne.|
|[zapisano](#saved)|Zwiększa liczbę bloków pamięci na liście bezpłatne.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<buforów >

**Namespace:** stdext

## <a name="allocated"></a>  max_fixed_size::allocated

Zwiększa liczbę bloków ilość przydzielonej pamięci.

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*_Nx*|Wartość przyrostu.|

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego nie działa. Ta funkcja członkowska jest wywoływana po każdym pomyślnym wywołaniem przez `cache_freelist::allocate` operatora **nowe**. Argument *_Nx* jest to liczba bloków pamięci we fragmencie przydzielonej przez operator **nowe**.

## <a name="deallocated"></a>  max_fixed_size::deallocated

Dekrementuje liczbę przydzielonych bloków pamięci.

```cpp
void deallocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*_Nx*|Wartość przyrostu.|

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego nie działa. Ta funkcja członkowska jest wywoływana po każdym wywołaniu przez `cache_freelist::deallocate` operatora **Usuń**. Argument *_Nx* jest to liczba bloków pamięci we fragmencie cofnięta przez operator **Usuń**.

## <a name="full"></a>  max_fixed_size::Full

Zwraca wartość określającą, czy więcej bloków pamięci powinna być dodana do listy bezpłatne.

```cpp
bool full();
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli `Max <= _Nblocks`; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest wywoływana przez `cache_freelist::deallocate`. Jeśli to wywołanie zwraca **true**, `deallocate` umieszcza blok pamięci na liście bezpłatne; Jeśli zostanie zwrócona wartość false, `deallocate` operatora wywołania **Usuń** można cofnąć alokacji bloku.

## <a name="max_fixed_size"></a>  max_fixed_size::max_fixed_size

Tworzy obiekt typu `max_fixed_size`.

```cpp
max_fixed_size();
```

### <a name="remarks"></a>Uwagi

Ten konstruktor inicjuje przechowywaną wartość `_Nblocks` do zera.

## <a name="released"></a>  max_fixed_size::released

Zmniejsza liczbę pamięci blokuje się na liście bezpłatne.

```cpp
void released();
```

### <a name="remarks"></a>Uwagi

Dekrementuje przechowywaną wartość `_Nblocks`. `released` Funkcja elementu członkowskiego bieżącego [maksymalnej liczby klas](../standard-library/allocators-header.md) jest wywoływana przez `cache_freelist::allocate` zawsze, gdy usunie blok pamięci z bezpłatnych listy.

## <a name="saved"></a>  max_fixed_size::Saved

Zwiększa liczbę bloków pamięci na liście bezpłatne.

```cpp
void saved();
```

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego zwiększa przechowywaną wartość `_Nblocks`. Ta funkcja członkowska jest wywoływana przez `cache_freelist::deallocate` zawsze umieszcza blok pamięci na liście bezpłatne.

## <a name="see-also"></a>Zobacz także

[\<allocators>](../standard-library/allocators-header.md)<br/>
