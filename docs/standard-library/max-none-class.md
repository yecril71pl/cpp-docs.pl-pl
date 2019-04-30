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
ms.openlocfilehash: 20191b84e4bbad760de1035fdb027fcbe827c874
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412946"
---
# <a name="maxnone-class"></a>max_none — Klasa

W tym artykule opisano [maksymalnej liczby klas](../standard-library/allocators-header.md) obiekt, który ogranicza [FreeList —](../standard-library/freelist-class.md) obiektu do maksymalnej długości równy zero.

## <a name="syntax"></a>Składnia

```cpp
template <std::size_t Max>
class max_none
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Maksymalna*|Maksymalna klasę, która określa maksymalną liczbę elementów do przechowywania w `freelist`.|

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

## <a name="allocated"></a>  max_none::allocated

Zwiększa liczbę bloków ilość przydzielonej pamięci.

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*_Nx*|Wartość przyrostu.|

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego nie działa. Jest wywoływane po każdym pomyślnym wywołaniem przez `cache_freelist::allocate` operatora **nowe**. Argument *_Nx* jest to liczba bloków pamięci we fragmencie przydzielonej przez operator **nowe**.

## <a name="deallocated"></a>  max_none::deallocated

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

## <a name="full"></a>  max_none::Full

Zwraca wartość określającą, czy więcej bloków pamięci powinna być dodana do listy bezpłatne.

```cpp
bool full();
```

### <a name="return-value"></a>Wartość zwracana

Ta funkcja członkowska jest zawsze zwraca **true**.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest wywoływana przez `cache_freelist::deallocate`. Jeśli to wywołanie zwraca **true**, `deallocate` umieszcza blok pamięci na liście bezpłatne; Jeśli zostanie zwrócona wartość false, `deallocate` operatora wywołania **Usuń** można cofnąć alokacji bloku.

## <a name="released"></a>  max_none::released

Zmniejsza liczbę pamięci blokuje się na liście bezpłatne.

```cpp
void released();
```

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego nie działa. `released` Funkcji składowej klasy bieżący maksymalny jest wywoływana przez `cache_freelist::allocate` zawsze, gdy usunie blok pamięci z bezpłatnych listy.

## <a name="saved"></a>  max_none::Saved

Zwiększa liczbę bloków pamięci na liście bezpłatne.

```cpp
void saved();
```

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego nie działa. Jest ona wywoływana przez `cache_freelist::deallocate` zawsze umieszcza blok pamięci na liście bezpłatne.

## <a name="see-also"></a>Zobacz także

[\<allocators>](../standard-library/allocators-header.md)<br/>
