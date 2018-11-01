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
ms.openlocfilehash: ba99d6ed3af34363bf88cde1a40e4bf37841cd8d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50555860"
---
# <a name="maxunbounded-class"></a>max_unbounded — Klasa

W tym artykule opisano [maksymalnej liczby klas](../standard-library/allocators-header.md) obiekt, który nie istnieje limit maksymalnego [FreeList —](../standard-library/freelist-class.md) obiektu.

## <a name="syntax"></a>Składnia

```cpp
class max_unbounded
```

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

## <a name="allocated"></a>  max_unbounded::allocated

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

## <a name="deallocated"></a>  max_unbounded::deallocated

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

## <a name="full"></a>  max_unbounded::Full

Zwraca wartość określającą, czy więcej bloków pamięci powinna być dodana do listy bezpłatne.

```cpp
bool full();
```

### <a name="return-value"></a>Wartość zwracana

Funkcja elementu członkowskiego zwraca zawsze **false**.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest wywoływana przez `cache_freelist::deallocate`. Jeśli to wywołanie zwraca **true**, `deallocate` umieszcza blok pamięci na liście bezpłatne; Jeśli zostanie zwrócona wartość false, `deallocate` operatora wywołania **Usuń** można cofnąć alokacji bloku.

## <a name="released"></a>  max_unbounded::released

Zmniejsza liczbę pamięci blokuje się na liście bezpłatne.

```cpp
void released();
```

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego nie działa. `released` Funkcji składowej klasy bieżący maksymalny jest wywoływana przez `cache_freelist::allocate` zawsze, gdy usunie blok pamięci z bezpłatnych listy.

## <a name="saved"></a>  max_unbounded::Saved

Zwiększa liczbę bloków pamięci na liście bezpłatne.

```cpp
void saved();
```

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego nie działa. Jest ona wywoływana przez `cache_freelist::deallocate` zawsze umieszcza blok pamięci na liście bezpłatne.

## <a name="see-also"></a>Zobacz także

[\<allocators — >](../standard-library/allocators-header.md)<br/>
